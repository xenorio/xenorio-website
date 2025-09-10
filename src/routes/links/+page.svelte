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
	<title>Xenorio | Links</title>
	<meta property="og:title" content="Xenorio | Links" />
	<meta property="og:description" content="Links to stuff™" />
	<meta property="og:url" content="https://xenorio.xyz/links" />
	<meta property="og:image" content="https://xenorio.xyz/img/avatar.png" />
</svelte:head>

<BackButton />

<div class="flex min-h-screen flex-col items-center justify-start px-4 pt-16">
	<h1 class="title-font mb-8 text-[45px] font-black" style="-webkit-text-stroke: 3px black; text-shadow: 0 0 10px rgba(0,0,0,0.8);">Links</h1>

	<ContentBox>
		<ul class="space-y-4 text-left text-[1.2rem]">
			<li>
				<a
					href="https://movies.xenorio.xyz"
					target="_blank"
					class="text-purple-400 hover:text-purple-300"
				>
					Xenorio's Movie and Series List
				</a> - Movies and series i enjoy
			</li>
			<li>
				<a
					href="https://music.xenorio.xyz"
					target="_blank"
					class="text-purple-400 hover:text-purple-300"
				>
					All da Music
				</a> - The music I listen to
			</li>
			<li>
				<a href="https://solhsa.com" target="_blank" class="text-purple-400 hover:text-purple-300">
					solhsa.com
				</a> - Sol's (aka Jari Komppa) blog, which i'm hosting
			</li>
		</ul>
	</ContentBox>
</div>
