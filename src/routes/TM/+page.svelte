<script>
    import CKC from '$lib/assets/TM/KC.jpg?url';
	import CMA from '$lib/assets/TM/MA.jpg?url';
	import MJ from '$lib/assets/TM/J.jpg?url';
	import PE from '$lib/assets/TM/E.jpg?url';

    // import Modal from './components/Modal.svelte';
    import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
    let showModal = false;
    let QKey = '';
	let Question = '';
    $: {
		let hasItem;
		onMount(async () => {
			hasItem = localStorage.getItem('letterKey') !== null;
			if (hasItem) {
				localStorage.removeItem('letterKey');
			}
		});
		// TM
		if (QKey == 'KC') {
			Question = import.meta.env.VITE_TM_KC_Q;
			showModal = true;
		} else if (QKey == 'MA') {
			Question = import.meta.env.VITE_TM_12_Q;
			showModal = true;
		} else if (QKey == 'J') {
			Question = import.meta.env.VITE_TM_10_Q;
			showModal = true;
		} else if (QKey == 'E') {
			Question = import.meta.env.VITE_TM_26_Q;
			showModal = true;
		}
    }
</script>
<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-img-redundant-alt -->
<div class="gridName">
    <h1 class="text-2xl mb-2 ml-5">Tourism Management</h1>
    <div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'KC')}>
        <img src={CKC} alt="N/A" class="object-cover ml-5 h-[150px] w-[150px] rounded-lg" />
        <p class="text-xl ml-4">
            3rd year <br /> TM-KC
        </p>
    </div>
    <div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'MA')}>
        <img src={CMA} alt="N/A" class="object-cover ml-5 h-[150px] w-[150px] rounded-lg" />
        <p class="text-xl ml-4">
            1st year <br /> TM-12
        </p>
    </div>
    <div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'J')}>
        <img src={MJ} alt="N/A" class="object-cover ml-5 h-[150px] w-[150px] rounded-lg" />
        <p class="text-xl ml-4">
            1st year <br /> TM-10
        </p>
    </div>
    <div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'E')}>
        <img src={PE} alt="N/A" class="object-cover ml-5 h-[150px] w-[150px] rounded-lg" />
        <p class="text-xl ml-4">
            1st year <br /> TM-26
        </p>
    </div>
</div>
<style lang="postcss">
	* {
		box-sizing: border-box;
	}
	.textWarning {
		color: #991b1b;
	}
	.gridName {
		float: left;
		width: 33.33%;
		padding: 10px;
	}
	.gridDesc {
		display: grid;
		grid-template-columns: 50% 50%;
		align-items: center;
		cursor: pointer;
	}
	@media screen and (max-width: 600px) {
		.gridName {
			width: 100%;
		}
	}
	:global(html) {
		background-color: theme(colors.bgBlack);
		color: #dddddd;
	}
</style>