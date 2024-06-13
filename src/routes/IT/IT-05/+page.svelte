<script>
	import EKJ from '$lib/assets/ITCS/KJ.jpg?url';
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
			if (hasItem && valueCheck == 'IT-05') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>

<div class="text-center m-5">Welcome, Estipona, K.</div>
<div class="cheatline text-center">Letter finished: June XX, 2024 | Letter written: June XX, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={EKJ} alt="N/A" class="object-cover mt-10 h-[260px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	
</article>
<article class="m-10 mb-3">
	
</article>
<article class="m-10 mb-3">
	
</article>
<footer class="m-10 mr-18 text-end">
	From your photographer, customer, and close friend, <br />
	Hanzyboy
</footer>
<button class="m-10 float-end border rounded-lg p-2" on:click={() => goto(base + '/')}>
	<Icon icon="ep:back" style="color: #dddddd" />
</button>

<style lang="postcss">
	.cheatline {
		background-color: #059142;
		color: #f5f3f3;
	}
	:global(html) {
		background-color: theme(colors.bgGreen);
		color: #dddddd;
	}
	@media screen and (max-width: 600px) {
		img {
			width: 77%;
		}
	}
</style>
