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
	interface Props {
		method: string;
		value: string;
		href: string;
	}

	let { method, value, href }: Props = $props();
</script>

<a {href} target="_blank" class="block transition-transform hover:scale-105">
	<div
		class="mx-auto mb-8 w-[75vw] max-w-4xl rounded-[19px] border-[6px] border-solid border-[#a452a3] bg-[rgb(59,59,59)] p-4 text-center"
	>
		<p class="mb-2 text-[2rem] font-bold text-purple-400">{method}</p>
		<p class="text-[1.2rem] text-purple-400">{value}</p>
	</div>
</a>

<style>
	@media (max-width: 768px) {
		p {
			font-size: 3vh;
		}
	}
</style>