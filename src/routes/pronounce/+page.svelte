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
	import BackButton from '$lib/components/BackButton.svelte';
	import ContentBox from '$lib/components/ContentBox.svelte';
</script>

<svelte:head>
	<title>Xenorio | Pronounce</title>
	<meta property="og:title" content="Pronouncing &quot;Xenorio&quot;" />
	<meta property="og:description" content="How to pronounce my name" />
	<meta property="og:url" content="https://xenorio.xyz/pronounce" />
	<meta property="og:image" content="https://xenorio.xyz/img/avatar.png" />
</svelte:head>

<BackButton />

<div class="flex min-h-screen flex-col items-center justify-start px-4 pt-16">
	<h1 class="title-font mb-8 text-[45px] font-black" style="-webkit-text-stroke: 3px black; text-shadow: 0 0 10px rgba(0,0,0,0.8);">Pronouncing "Xenorio"</h1>

	<ContentBox>
		<div class="space-y-6">
			<div>
				<h2 class="mb-4 text-[30px]">English:</h2>
				<audio src="/sound/xenorio-en.mp3" controls class="mx-auto"></audio>
			</div>

			<div>
				<h2 class="mb-4 text-[30px]">German:</h2>
				<audio src="/sound/xenorio-de.mp3" controls class="mx-auto"></audio>
			</div>
		</div>
	</ContentBox>
</div>
