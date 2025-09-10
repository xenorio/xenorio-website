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
	import '../app.css';
	import '@fortawesome/fontawesome-free/css/all.css';
	import ParticleBackground from '$lib/components/ParticleBackground.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/img/avatar.png" />
	<meta name="theme-color" content="#6441A4" />
</svelte:head>

<ParticleBackground />

<main class="relative z-10 min-h-screen text-center">
	{@render children?.()}
</main>
