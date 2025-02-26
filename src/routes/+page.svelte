<script>
	import { base } from '$app/paths';
	import Modal from './components/Modal.svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { Card, Button, Label, Input, Checkbox } from 'flowbite-svelte';
	let showModal = false;
	let QKey = '';
	let Question = '';
	let Answer = '';
	let pHolder = 'Use proper capitalization please.';
	const answerCheck = () => {
		//TM
		if (QKey == 'KC' && Answer == import.meta.env.VITE_TM_KC_A1 || QKey == 'KC' && Answer == import.meta.env.VITE_TM_KC_A2) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_KC_T);
			goto(base + '/TM/TM-KC');
		} else if (QKey == 'MA' && Answer == import.meta.env.VITE_TM_12_A1 || QKey == 'MA' && Answer == import.meta.env.VITE_TM_12_A2) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_12_T);
			goto(base + '/TM/TM-12');
		} else if (QKey == 'J' && Answer == import.meta.env.VITE_TM_10_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_10_T);
			goto(base + '/TM/TM-10');
		} else if (QKey == 'E' && Answer == import.meta.env.VITE_TM_26_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_26_T);
			goto(base + '/TM/TM-26');
		}  else if (QKey == 'LJ' && Answer == import.meta.env.VITE_TM_F_12_A1 || QKey == 'LJ' && Answer == import.meta.env.VITE_TM_F_12_A2 || QKey == 'LJ' && Answer == import.meta.env.VITE_TM_F_12_A3) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_F_12_T);
			goto(base + '/TM/TM-F-12');
		}
		//ITCS
		else if (QKey == 'KJ' && Answer == import.meta.env.VITE_IT_05_A1 || QKey == 'KJ' && Answer == import.meta.env.VITE_IT_05_A2) {
			localStorage.setItem('letterKey', import.meta.env.VITE_IT_05_T);
			goto(base + '/IT/IT-05');
		} else if (QKey == 'MK' && Answer == import.meta.env.VITE_CS_15_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_CS_15_T);
			goto(base + '/CS/CS-15');
		} else if (QKey == 'MMP' && Answer == import.meta.env.VITE_IT_12_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_IT_12_T);
			goto(base + '/IT/IT-12');
		} else if (QKey == 'CF' && Answer == import.meta.env.VITE_IT_26_A1 || QKey == 'CF' && Answer == import.meta.env.VITE_IT_26_A2) {
			localStorage.setItem('letterKey', import.meta.env.VITE_IT_26_T);
			goto(base + '/IT/IT-F-26');
		} else if (QKey == 'SA/WD' && Answer == import.meta.env.VITE_DevPass) {
			localStorage.setItem('letterKey', import.meta.env.VITE_SiteKey);
			goto(base + '/IT/IT-00');
		} else if (QKey == 'JB' && Answer == import.meta.env.VITE_IT_20_A1 || QKey == 'JB' && Answer == import.meta.env.VITE_IT_20_A2) {
			localStorage.setItem('letterKey', import.meta.env.VITE_IT_20_T);
			goto(base + '/IT/IT-F-20');
		}
		//NTS
		else if (QKey == 'Q' && Answer == import.meta.env.VITE_GA_15_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_GA_15_T);
			goto(base + '/NTS/GA-15');
		} else if (QKey == 'SL-A' && Answer == import.meta.env.VITE_SL_24_A1 || QKey == 'SL-A' && Answer == import.meta.env.VITE_SL_24_A2) {
			localStorage.setItem('letterKey', import.meta.env.VITE_SL_24_T);
			goto(base + '/NTS/SL-24');
		} else if (QKey == 'SN-A' && Answer == import.meta.env.VITE_SN_19_A1 || QKey == 'SN-A' && Answer == import.meta.env.VITE_SN_19_A2) {
			localStorage.setItem('letterKey', import.meta.env.VITE_SN_19_T);
			goto(base + '/NTS/SN-19');
		}
		else if (Answer == '')
		{
			pHolder = "Preferably with an answer.";
		}
		else
		{
			pHolder = 'Try again.';
		}
		Answer = '';
	};
	$: {
		let hasItem;
		pHolder = 'Use proper capitalization please.';
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
		} else if (QKey == 'LJ') {
			Question = import.meta.env.VITE_TM_F_12_Q;
			showModal = true;
		} else if (QKey == 'SA/WD') {
			Question = "Your password please.";
			showModal = true;
		}
		//ITCS
		else if (QKey == 'KJ') {
			Question = import.meta.env.VITE_IT_05_Q;
			showModal = true;
		} else if (QKey == 'MK') {
			Question = import.meta.env.VITE_CS_15_Q;
			showModal = true;
		} else if (QKey == 'MMP') {
			Question = import.meta.env.VITE_IT_12_Q;
			showModal = true;
		} else if (QKey == 'CF') {
			Question = import.meta.env.VITE_IT_26_Q;
			showModal = true;
		} else if (QKey == 'JB') {
			Question = import.meta.env.VITE_IT_20_Q;
			showModal = true;
		}
		//NTS
		else if (QKey == 'Q') {
			Question = import.meta.env.VITE_GA_15_Q;
			showModal = true;
		} else if (QKey == 'SL-A') {
			Question = import.meta.env.VITE_SL_24_Q;
			showModal = true;
		} else if (QKey == 'SN-A') {
			Question = import.meta.env.VITE_SN_19_Q;
			showModal = true;
		}
	}
</script>
<title>Letter Storage System</title>
<h1 class="text-3xl text-center m-9 mb-4">Welcome</h1>
<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-img-redundant-alt -->
<div>
	<h1 class="text-lg m-2 text-center">Please select your Year/Course or work in the list below</h1>
	<h1 class="text-lg m-2 text-center">Note: <span class="text-[#eed202]">Yellow coded </span>= under development | <span class="text-green-400">Light Green coded</span> = New UI</h1>
	<!-- TM -->
	<div class="gridName text-center">
		<h1 class="text-2xl mb-2">Tourism Management</h1>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'KC')}>
			<p class="text-xl text-green-400">
				4th year | TM-KC
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5 " on:click={() => (QKey = 'MA')}>
			<p class="text-xl text-green-400">
				2nd year | TM-12
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'J')}>
			<p class="text-xl text-green-400">
				2nd year | TM-10
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'E')}>
			<p class="text-xl text-green-400">
				2nd year | TM-26
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'LJ')}>
			<p class="text-xl">
				Faculty | TM-F-12
			</p>
		</div>
	</div>
	<!-- IT/CS -->
	<div class="gridName text-center">
		<h1 class="text-2xl mb-2">ICT</h1>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'KJ')}>
			<p class="text-xl text-green-400">
				4th year | IT | IT-05
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'MK')}>
			<p class="text-xl text-green-400">
				3rd year | CS | CS-15
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'MMP')}>
			<p class="text-xl">
				Alumnus | IT | IT-2024-12
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'CF')}>
			<p class="text-xl">
				Faculty | IT | IT-F-26
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'JB')}>
			<p class="text-xl text-[#eed202]">
				Former faculty | IT | IT-F-20
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'SA/WD')}>
			<p class="text-xl">
				Alumnus | IT | IT-2020-2024-05
			</p>
		</div>
		<!-- <div class="gridDesc flex overflow-hidden mb-5 text-center" on:click={() => (goto(base + '/STI'))}>
			<p class="text-xl">
				Final letter
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5 text-center" on:click={() => (goto(base + '/FF'))}>
			<p class="text-xl">
				Family and friends
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5 text-center" on:click={() => (goto(base + '/BirthdayMessages'))}>
			<p class="text-xl">
				Send your bithday greetings here
			</p>
		</div> -->
	</div>
	<!-- NTS -->
	<div class="gridName text-center">
		<h1 class="text-2xl mb-2">Non-Teaching Staff</h1>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'Q')}>
			<p class="text-xl">
				Former Guidance Associate | GA-15
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'SL-A')}>
			<p class="text-xl text-green-400">
				School Librarian | SL-24
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'SN-A')}>
			<p class="text-xl">
				School Nurse | SN-19
			</p>
		</div>
	</div>
</div>
{#if QKey}
<Modal bind:showModal>
	<h2 slot="header" class="text-2xl text-center border-b-2 border-bgBlack">Passphrase</h2>
	<p class="text-base text-center text-[#991b1b]">{pHolder}</p>
	<p class="text-base text-center">{Question}</p>
	<form on:submit|preventDefault={answerCheck} class="text-center">
		<input type="text" class="border-b-2 rounded-sm my-2" placeholder="Answer" bind:value={Answer} />
		<hr />
		<button class="inline-flex w-full justify-center border-t-2 border-b-2 border-bgBlack font-medium text-sm px-5 py-2.5 text-center">
			Submit
		</button>
	</form>
</Modal>
{/if}
<style lang="postcss">
	.gridName {
		float: left;
		width: 33.33%;
		padding: 10px;
	}
	.gridDesc {
		/* display: grid;
		grid-template-columns: 50% 50%;
		align-items: center; */
		display: grid;
		cursor: pointer;
    	justify-content: center;
	}
  .gridDesc:hover
  {
    text-decoration: underline;
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