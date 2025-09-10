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
</script>

<svelte:head>
	<title>Xenorio | Legal Disclosure</title>
	<meta property="og:title" content="Xenorio's Legal Disclosure" />
	<meta property="og:description" content="Who even reads this?" />
	<meta property="og:url" content="https://xenorio.xyz/disclosure" />
	<meta property="og:image" content="https://xenorio.xyz/img/avatar.png" />
</svelte:head>

<BackButton />

<div class="flex min-h-screen flex-col items-center justify-start px-4 pt-16">
	<h1 class="title-font mb-8 text-[45px] font-black" style="-webkit-text-stroke: 3px black; text-shadow: 0 0 10px rgba(0,0,0,0.8);">Legal Disclosure</h1>

	<div
		class="mx-auto mb-8 w-[75vw] max-w-4xl rounded-[19px] border-[6px] border-solid border-[#a452a3] bg-[rgb(59,59,59)] p-4"
	>
		<h3 class="text-left text-[25px] leading-relaxed">
			Information in accordance with the Digital Services Act
			<br /><br />
			<strong class="underline decoration-[#a452a3] underline-offset-2">Site Owner</strong><br /><br />
			Marcus Huber<br />
			Trading as Xenorio Industries<br />
			Sudermannstraße 9<br />
			38226 Salzgitter, Germany<br />
			<br /><strong class="underline decoration-[#a452a3] underline-offset-2"
				>Contact Information</strong
			><br /><br />
			Business inquiries:
			<a href="mailto:business@xenorio.xyz" class="text-purple-400 hover:text-purple-300"
				>business@xenorio.xyz</a
			><br />
			Phone: +49 172 907 5536
			<br />
			<br /><strong class="underline decoration-[#a452a3] underline-offset-2"
				>Content Responsibility</strong
			><br /><br />
			I am fully responsible for all content on this website.<br />
			I am not obligated to monitor transmitted or saved information of third parties.<br
			/>
			I will investigate circumstances pointing to illegal activity when made aware of them.

			<br /><br /><strong class="underline decoration-[#a452a3] underline-offset-2"
				>External Links</strong
			><br /><br />
			Responsibility for content on linked third-party websites lies with their respective operators.<br />
			At the time of linking, no violations were evident. I will remove links if violations are brought to my attention.

			<br /><br /><strong class="underline decoration-[#a452a3] underline-offset-2"
				>Data Protection</strong
			><br /><br />
			This website does not collect, store, or process any personal data.<br />
			No logs are maintained and no analytics are performed.<br />
			No data is ever transferred to third parties.<br /><br />
			This website is hosted in Finland (EU).

			<br /><br /><strong class="underline decoration-[#a452a3] underline-offset-2">Cookies</strong
			><br /><br />
			This website does not use cookies or any tracking technologies.

			<br /><br /><strong class="underline decoration-[#a452a3] underline-offset-2"
				>Copyright & Licensing</strong
			><br /><br />
			The source code of this website is available on
			<a
				href="https://github.com/Xenorio/xenorio-website"
				target="_blank"
				class="text-purple-400 hover:text-purple-300">GitHub</a
			>
			under the
			<a
				href="https://github.com/Xenorio/xenorio-website/blob/main/LICENSE"
				target="_blank"
				class="text-purple-400 hover:text-purple-300">AGPLv3 license</a
			>.<br /><br />
			
			The TARDIS 3D model used on this website is by 
			<a
				href="https://sketchfab.com/3d-models/doctor-who-tardis-bb035ac75cdd4dd688fe5b73da591d14"
				target="_blank"
				class="text-purple-400 hover:text-purple-300">LCrowsbeak</a
			> 
			and is licensed under 
			<a
				href="https://creativecommons.org/licenses/by/4.0/"
				target="_blank"
				class="text-purple-400 hover:text-purple-300">CC BY 4.0</a
			>.
		</h3>
	</div>
</div>
