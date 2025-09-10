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
	
	const birthDate = new Date(2000, 6, 3);
	const today = new Date();
	let age = today.getFullYear() - birthDate.getFullYear();
	const monthDiff = today.getMonth() - birthDate.getMonth();
	if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < birthDate.getDate())) {
		age--;
	}
</script>

<svelte:head>
	<title>Xenorio | About</title>
	<meta property="og:title" content="About Xenorio" />
	<meta
		property="og:description"
		content="Information about a random guy you found on the internet"
	/>
	<meta property="og:url" content="https://xenorio.xyz/about" />
	<meta property="og:image" content="https://xenorio.xyz/img/avatar.png" />
</svelte:head>

<BackButton />

<div class="flex min-h-screen flex-col items-center justify-start px-4 pt-16">
	<h1 class="title-font mb-8 text-[45px] font-black max-sm:text-[35px]" style="-webkit-text-stroke: 3px black; text-shadow: 0 0 10px rgba(0,0,0,0.8);">About</h1>

	<ContentBox>
		<h1 class="mb-4 text-[35px] max-sm:text-[28px]">Hey there!</h1>

		<h2 class="text-center text-[25px] leading-relaxed max-sm:text-[20px] max-sm:leading-normal">
			I'm Marcus - though most people online know me as Xenorio. I'm a {age}-year-old DevOps engineer currently living in Salzgitter, Germany. I've been messing around with computers since I was 6 years old, starting with an "HTML for Kids" book that my parents probably regretted buying me.<br /><br />
			
			IT isn't just my job, it's pretty much my entire existence. When I'm not working on computer stuff, I'm... well, probably still doing computer stuff. Or watching YouTube. I don't really have other hobbies, but honestly that works out great since I love what I do.<br /><br />
			
			These days I'm all about JavaScript and TypeScript, though I have a burning hatred for Java and PHP. I use Arch btw, because of course I do. I'm also a huge Doctor Who fan, and I've got 
			<a href="https://movies.xenorio.xyz" target="_blank" class="text-purple-400 hover:text-purple-300">lists of movies</a> 
			and 
			<a href="https://music.xenorio.xyz" target="_blank" class="text-purple-400 hover:text-purple-300">music</a> 
			if you want to see what weird stuff I'm into.<br /><br />
			
			I'm neurodivergent, which means my brain works a bit differently than most people's. My sleep schedule is basically "sleep when tired, wake when not tired", which mostly gravitates towards being awake at night. I don't read books at all, prefer mate over coffee, and have some pretty strong left-leaning political views about everything from trash bin systems to, well, most aspects of how society should work.<br /><br />
			
			If you're wondering how to pronounce my username, there's literally a 
			<a href="/pronounce" class="text-purple-400 hover:text-purple-300">whole page for that</a> 
			because apparently "Xenorio" isn't as obvious as I thought it was.
		</h2>
	</ContentBox>
</div>
