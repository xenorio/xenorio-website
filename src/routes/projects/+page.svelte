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
	import ProjectCard from '$lib/components/ProjectCard.svelte';
</script>

<svelte:head>
	<title>Xenorio | Projects</title>
	<meta property="og:title" content="Xenorio's Projects" />
	<meta property="og:description" content="May include something cool" />
	<meta property="og:url" content="https://xenorio.xyz/projects" />
	<meta property="og:image" content="https://xenorio.xyz/img/avatar.png" />
</svelte:head>

<BackButton />

<div class="flex min-h-screen flex-col items-center justify-start px-4 pt-16">
	<h1 class="title-font mb-8 text-[45px] font-black" style="-webkit-text-stroke: 3px black; text-shadow: 0 0 10px rgba(0,0,0,0.8);">Active Projects</h1>

	<ProjectCard
		href="https://research-community.org"
		title="Research Community"
		subtitle="Education and harm reduction on research chemicals and other psychoactive substances"
	/>

	<ProjectCard
		href="https://gesichertdemokratisch-muenden.de"
		title="Gesichert Demokratisch Münden"
		subtitle="German political group for which I do IT stuff"
	/>

	<ProjectCard
		href="https://die-linke-salzgitter.de"
		title="Die Linke Salzgitter"
		subtitle='Homepage of the Salzgitter division of the german political party "Die Linke"'
	/>

	<h1 class="title-font mt-8 mb-4 text-[45px] font-black" style="-webkit-text-stroke: 3px black; text-shadow: 0 0 10px rgba(0,0,0,0.8);">Archived Projects</h1>
	<h3 class="mb-8 text-[25px]">These projects are discontinued</h3>

	<ProjectCard
		href="https://github.com/Xenorio/ScamAway"
		title="ScamAway"
		subtitle="The Anti-Phishing Discord Bot"
	/>

	<ProjectCard
		href="https://github.com/Xenorio/HomebrewDUC"
		title="HomebrewDUC"
		subtitle="Modular DynDNS update client"
	/>

	<ProjectCard
		href="https://github.com/Xenorio/Twitch_DeleteLog"
		title="Twitch_DeleteLog"
		subtitle="Logs deleted Twitch messages"
	/>

	<ProjectCard
		title="YingaGaming"
		subtitle="German gaming community and Minecraft Server"
	/>
</div>
