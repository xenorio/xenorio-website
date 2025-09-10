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
	import TardisAnimation from '$lib/components/TardisAnimation.svelte';
	import { browser } from '$app/environment';

	let tardisAnimation: TardisAnimation;
	let isLargeScreen = true;

	function handleTitleClick() {
		if (tardisAnimation && isLargeScreen) {
			tardisAnimation.triggerAnimation();
		}
	}

	function checkScreenSize() {
		if (browser) {
			isLargeScreen = window.innerWidth >= 768;
		}
	}
	if (browser) {
		checkScreenSize();
		window.addEventListener('resize', checkScreenSize);
	}
</script>

<svelte:head>
	<title>Xenorio</title>
	<meta property="og:title" content="Xenorio's Website" />
	<meta property="og:description" content="Where great stuff is being done, maybe" />
	<meta property="og:url" content="https://xenorio.xyz" />
	<meta property="og:image" content="https://xenorio.xyz/img/avatar.png" />
</svelte:head>

<div class="flex min-h-screen flex-col items-center px-4">
	{#if isLargeScreen}
		<button 
			class="mt-[25vh] mb-6 bg-transparent border-none p-0 transition-transform hover:scale-105 active:scale-95 cursor-pointer"
			on:click={handleTitleClick}
		>
			<img 
				src="/img/TitleImage.png" 
				alt="Xenorio" 
				class="max-w-[90vw]" 
			/>
		</button>
	{:else}
		<img 
			src="/img/TitleImage.png" 
			alt="Xenorio" 
			class="mt-[25vh] mb-6 max-w-[90vw]" 
		/>
	{/if}

	<nav class="mb-4">
		<div id="links" class="text-[35px] font-black" style="-webkit-text-stroke: 2px black;">
			<a href="/about" class="text-purple-400 transition-colors hover:text-purple-300">About</a>
			<span class="linkdivider mx-2 max-md:hidden">|</span>
			<a href="/projects" class="text-purple-400 transition-colors hover:text-purple-300">Projects</a>
			<span class="linkdivider mx-2 max-md:hidden">|</span>
			<a href="/links" class="text-purple-400 transition-colors hover:text-purple-300">Links</a>
			<span class="linkdivider mx-2 max-md:hidden">|</span>
			<a href="/contact" class="text-purple-400 transition-colors hover:text-purple-300">Contact</a>
		</div>
	</nav>

	<div id="quicklinks" class="mt-4 space-x-4 text-5xl max-sm:space-x-3 max-sm:text-4xl">
		<a
			href="https://github.com/Xenorio"
			target="_blank"
			title="GitHub"
			aria-label="GitHub"
			class="inline-block transition-transform hover:scale-110"
		>
			<i class="fa-brands fa-github"></i>
		</a>
		<a
			href="https://telegram.xenorio.xyz"
			target="_blank"
			title="Telegram"
			aria-label="Telegram"
			class="inline-block transition-transform hover:scale-110"
		>
			<i class="fa-brands fa-telegram text-[#0088cc]"></i>
		</a>
		<a
			rel="me"
			href="https://mastodon.social/@xenorio"
			target="_blank"
			title="Mastodon"
			aria-label="Mastodon"
			class="inline-block transition-transform hover:scale-110"
		>
			<i class="fa-brands fa-mastodon text-[#5a47dc]"></i>
		</a>
		<a
			href="mailto:hi@xenorio.xyz"
			target="_blank"
			title="E-Mail"
			aria-label="E-Mail"
			class="inline-block transition-transform hover:scale-110"
		>
			<i class="fa-solid fa-envelope text-yellow-400"></i>
		</a>
		<a
			href="https://steam.xenorio.xyz"
			target="_blank"
			title="Steam"
			aria-label="Steam"
			class="inline-block transition-transform hover:scale-110"
		>
			<i class="fa-brands fa-steam"></i>
		</a>
	</div>

	<a
		href="/disclosure"
		class="absolute right-2 bottom-2 text-base text-purple-400 hover:text-purple-300 max-sm:text-sm max-sm:right-1 max-sm:bottom-1"
	>
		Legal Disclosure
	</a>
</div>

{#if isLargeScreen}
	<TardisAnimation bind:this={tardisAnimation} />
{/if}

<style>
	#links a {
		text-decoration: none;
	}

	@media (max-width: 768px) {
		#links {
			font-size: 3rem;
			-webkit-text-stroke: none;
		}
	}
	
	@media (max-width: 640px) {
		#links {
			font-size: 2.5rem;
		}
	}
</style>
