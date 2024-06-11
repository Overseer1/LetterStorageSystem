<script>
	import PE from '$lib/assets/TM/E.jpg?url';
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
			if (hasItem && valueCheck == 'TM-26') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>

<div class="text-center m-5">Welcome, Pagulayan, E.</div>
<div class="cheatline text-center">Letter finished: June XX, 2024 | Letter written: N/A</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={PE} alt="N/A" class="object-cover mt-10 h-[250px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	
</article>
<article class="m-10 mb-3">
	
</article>
<article class="m-10 mb-3">
	
</article>
<button class="m-10 float-end border rounded-lg p-2" on:click={() => goto(base + '/')}>
	<Icon icon="ep:back" style="color: #dddddd" />
</button>

<style lang="postcss">
	.cheatline {
		background-color: #dddddd;
		color: #313131;
	}
	:global(html) {
		background-color: theme(colors.bgBlackWhite);
		color: #dddddd;
	}
	@media screen and (max-width: 600px) {
		img {
			width: 77%;
		}
	}
</style>
