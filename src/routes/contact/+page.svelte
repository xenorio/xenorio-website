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
	import ContactCard from '$lib/components/ContactCard.svelte';
</script>

<svelte:head>
	<title>Xenorio | Contact</title>
	<meta property="og:title" content="Xenorio's Contact Info" />
	<meta property="og:description" content="E.T. Phone Home" />
	<meta property="og:url" content="https://xenorio.xyz/contact" />
	<meta property="og:image" content="https://xenorio.xyz/img/avatar.png" />
</svelte:head>

<BackButton />

<div class="flex min-h-screen flex-col items-center justify-start px-4 pt-16">
	<h1 class="title-font mb-8 text-[45px] font-black max-sm:text-[35px]" style="-webkit-text-stroke: 3px black; text-shadow: 0 0 10px rgba(0,0,0,0.8);">Contact</h1>

	<ContactCard
		method="E-Mail"
		value="hi@xenorio.xyz"
		href="mailto:hi@xenorio.xyz"
	/>

	<ContactCard
		method="Signal"
		value="xenorio.69420"
		href="https://signal.me/#eu/ti5lSmkPYR5a8WLXa8euC2P9v80rhR0BiYdSfAOGi3oR16tRdwFOKqsyOIOgX1oh"
	/>

	<ContactCard
		method="Telegram"
		value="Xenorio"
		href="https://telegram.xenorio.xyz"
	/>
</div>
