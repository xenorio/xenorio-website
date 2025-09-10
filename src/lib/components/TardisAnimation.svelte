<!--
 Copyright (C) 2025 xenorio <dev@xenorio.xyz>
 
 This program is free software: you can redistribute it and/or modify
 it under the terms of the GNU Affero General Public License as
 published by the Free Software Foundation, either version 3 of the
 License, or (at your option) any later version.
 
 This program is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU Affero General Public License for more details.
 
 You should have received a copy of the GNU Affero General Public License
 along with this program.  If not, see <http://www.gnu.org/licenses/>.
-->

<script lang="ts">
	import { onMount } from 'svelte';
	import * as THREE from 'three';
	import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js';

	const FLIGHT_CONFIG = {
		centerWidth: 10, centerHeight: 6,
		boundaryWidth: 5, boundaryHeight: 3,
		maxSpeed: 0.05, steeringForce: 0.01,
		bounceForce: 0.02, wobbleChance: 0.1,
		wobbleAmount: 0.005, exitBuffer: 4.0,
		rotationSpeed: 0.05, wobbleFreq: 0.002, wobbleAmp: 0.015
	};

	let container: HTMLDivElement;
	let scene: THREE.Scene;
	let camera: THREE.PerspectiveCamera;
	let renderer: THREE.WebGLRenderer;
	let tardis: THREE.Object3D;
	let animationId: number;
	let isAnimating = false;
	let audio: HTMLAudioElement;
	let isExiting = false;
	let exitStartTime: number = 0;
	let animationStartTime: number = 0;
	let flightData: {
		currentX: number; currentY: number;
		velocityX: number; velocityY: number;
		targetX: number; targetY: number;
		exitX: number; exitY: number;
	};

	export function triggerAnimation() {
		if (isAnimating) return;
		startTardisAnimation();
	}

	onMount(() => {
		initThreeJS();
		loadTardis();
		
		return () => {
			if (animationId) {
				cancelAnimationFrame(animationId);
			}
			if (renderer) {
				renderer.dispose();
			}
		};
	});

	function initThreeJS() {
		scene = new THREE.Scene();

		camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
		camera.position.set(0, 0, 5);
		camera.lookAt(0, 0, 0);

		renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true });
		renderer.setSize(window.innerWidth, window.innerHeight);
		renderer.setClearColor(0x000000, 0);
		
		container.appendChild(renderer.domElement);

		const ambientLight = new THREE.AmbientLight(0x404040, 0.6);
		scene.add(ambientLight);

		const directionalLight = new THREE.DirectionalLight(0xffffff, 0.8);
		directionalLight.position.set(1, 1, 1);
		scene.add(directionalLight);

		window.addEventListener('resize', onWindowResize, false);
	}

	function loadTardis() {
		const loader = new GLTFLoader();
		loader.load(
			'/tardis.glb',
			(gltf) => {
				tardis = gltf.scene;
				
				tardis.scale.set(0.3, 0.3, 0.3);
				tardis.position.set(-10, 0, 0);
				tardis.visible = false;
				
				scene.add(tardis);
			},
			(progress) => {
				console.log('TARDIS loading progress:', (progress.loaded / progress.total * 100) + '%');
			},
			(error) => {
				console.error('Error loading TARDIS:', error);
			}
		);
	}

	function generateRandomTarget() {
		return {
			x: (Math.random() - 0.5) * FLIGHT_CONFIG.centerWidth,
			y: (Math.random() - 0.5) * FLIGHT_CONFIG.centerHeight
		};
	}

	function generateEdgePosition(isStartPosition = false) {
		const edges = ['top', 'bottom', 'left', 'right'] as const;
		const edge = edges[Math.floor(Math.random() * edges.length)];
		
		const positions: Record<typeof edges[number], { x: number; y: number }> = {
			left: { x: -12, y: (Math.random() - 0.5) * 6 },
			right: { x: 12, y: (Math.random() - 0.5) * 6 },
			top: { x: (Math.random() - 0.5) * (isStartPosition ? 10 : 16), y: 6 },
			bottom: { x: (Math.random() - 0.5) * (isStartPosition ? 10 : 16), y: -6 }
		};
		
		return positions[edge];
	}

	function initializeFlightData() {
		const start = generateEdgePosition(true);
		const target = generateRandomTarget();
		const exit = generateEdgePosition(false);
		
		return {
			currentX: start.x, currentY: start.y,
			velocityX: 0, velocityY: 0,
			targetX: target.x, targetY: target.y,
			exitX: exit.x, exitY: exit.y
		};
	}

	function applySteeringToTarget(targetX: number, targetY: number) {
		const dx = targetX - flightData.currentX;
		const dy = targetY - flightData.currentY;
		const distance = Math.sqrt(dx * dx + dy * dy);
		
		let desiredVelX = 0, desiredVelY = 0;
		if (distance > 0.01) {
			desiredVelX = (dx / distance) * FLIGHT_CONFIG.maxSpeed;
			desiredVelY = (dy / distance) * FLIGHT_CONFIG.maxSpeed;
		}
		
		flightData.velocityX += (desiredVelX - flightData.velocityX) * FLIGHT_CONFIG.steeringForce;
		flightData.velocityY += (desiredVelY - flightData.velocityY) * FLIGHT_CONFIG.steeringForce;
		
		const currentSpeed = Math.sqrt(flightData.velocityX ** 2 + flightData.velocityY ** 2);
		if (currentSpeed > FLIGHT_CONFIG.maxSpeed) {
			flightData.velocityX = (flightData.velocityX / currentSpeed) * FLIGHT_CONFIG.maxSpeed;
			flightData.velocityY = (flightData.velocityY / currentSpeed) * FLIGHT_CONFIG.maxSpeed;
		}
		
		return distance;
	}

	function applyBoundaryForces() {
		const { boundaryWidth, boundaryHeight, bounceForce } = FLIGHT_CONFIG;
		
		if (flightData.currentX > boundaryWidth) {
			flightData.velocityX -= (flightData.currentX - boundaryWidth) * bounceForce;
		} else if (flightData.currentX < -boundaryWidth) {
			flightData.velocityX += (-boundaryWidth - flightData.currentX) * bounceForce;
		}
		
		if (flightData.currentY > boundaryHeight) {
			flightData.velocityY -= (flightData.currentY - boundaryHeight) * bounceForce;
		} else if (flightData.currentY < -boundaryHeight) {
			flightData.velocityY += (-boundaryHeight - flightData.currentY) * bounceForce;
		}
	}

	function startTardisAnimation() {
		if (!tardis || isAnimating) return;
		
		if (animationId) cancelAnimationFrame(animationId);
		
		flightData = initializeFlightData();
		
		audio = new Audio('/sound/tardis.mp3');
		audio.addEventListener('loadedmetadata', () => {
			exitStartTime = Math.max(0, (audio.duration - FLIGHT_CONFIG.exitBuffer) * 1000);
		});
		audio.addEventListener('ended', () => {
			if (isAnimating && !isExiting) isExiting = true;
		});
		audio.play().catch(console.error);
		
		isAnimating = true;
		isExiting = false;
		tardis.visible = true;
		animationStartTime = Date.now();
		tardis.position.set(flightData.currentX, flightData.currentY, 0);
		tardis.rotation.set(0, 0, 0);
		
		animate();
	}

	function animate() {
		if (tardis && isAnimating) {
			tardis.rotation.y += FLIGHT_CONFIG.rotationSpeed;
			
			tardis.rotation.x = Math.sin(Date.now() * FLIGHT_CONFIG.wobbleFreq) * FLIGHT_CONFIG.wobbleAmp;
			
			if (!isExiting && exitStartTime > 0) {
				const elapsedTime = Date.now() - animationStartTime;
				if (elapsedTime >= exitStartTime) {
					isExiting = true;
				}
			}
			
			if (isExiting) {
				const distance = applySteeringToTarget(flightData.exitX, flightData.exitY);
				
				if (distance < 0.5) {
					tardis.visible = false;
					isAnimating = false;
					cancelAnimationFrame(animationId);
					return;
				}
				
				flightData.currentX += flightData.velocityX;
				flightData.currentY += flightData.velocityY;
				
			} else {
				const distance = applySteeringToTarget(flightData.targetX, flightData.targetY);
				
				if (distance < 0.8) {
					const newTarget = generateRandomTarget();
					flightData.targetX = newTarget.x;
					flightData.targetY = newTarget.y;
				}
				
				flightData.currentX += flightData.velocityX;
				flightData.currentY += flightData.velocityY;
				
				if (Math.random() < FLIGHT_CONFIG.wobbleChance) {
					flightData.currentX += (Math.random() - 0.5) * FLIGHT_CONFIG.wobbleAmount;
					flightData.currentY += (Math.random() - 0.5) * FLIGHT_CONFIG.wobbleAmount;
				}
				
				applyBoundaryForces();
			}
			
			tardis.position.x = flightData.currentX;
			tardis.position.y = flightData.currentY;
		}

		if (renderer && scene && camera) {
			renderer.render(scene, camera);
		}

		if (isAnimating) {
			animationId = requestAnimationFrame(animate);
		}
	}

	function onWindowResize() {
		camera.aspect = window.innerWidth / window.innerHeight;
		camera.updateProjectionMatrix();
		renderer.setSize(window.innerWidth, window.innerHeight);
	}
</script>

<div bind:this={container} class="fixed inset-0 z-0 pointer-events-none"></div>