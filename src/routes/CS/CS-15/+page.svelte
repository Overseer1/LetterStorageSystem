<script>
	import MMK from '$lib/assets/ITCS/MK.jpg?url';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	$: {
		let hasItem;
		let valueCheck;
		onMount(async () => {
			hasItem = localStorage.getItem('letterKey') !== null;
			valueCheck = localStorage.getItem('letterKey');
			// Conditional logic based on hasItem
			if (hasItem && valueCheck == 'CS-15') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>

<div class="text-center m-5">Welcome, Marson, M. K.</div>
<div class="cheatline text-center">Letter finished: June XX, 2024 | Letter written: N/A</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={MMK} alt="N/A" class="object-cover mt-10 h-[400px] w-[250px] rounded-lg" />
</header>
<h1 class="text-center">*insert final letter here</h1>
<footer class="m-10 mr-18 text-end">
	From your school twin brother, co-photographer, and close friend, <br />
	Hanz
</footer>
<button class="m-10 float-end border rounded-lg p-2" on:click={() => goto(base + '/')}>
	<Icon icon="ep:back" style="color: #dddddd" />
</button>

<style lang="postcss">
	.cheatline {
		background-color: #fd5da8;
		color: #eeeeee;
	}
	:global(html) {
		background-color: theme(colors.bgPink);
		color: #dddddd;
	}
	@media screen and (max-width: 600px) {
		img {
			width: 77%;
		}
	}
</style>
