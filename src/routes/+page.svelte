<script>
	import { base } from '$app/paths';
	import Modal from './components/Modal.svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';

	let showModal = false;
	let QKey = '';
	let Question = '';
	let Answer = '';
	let pHolder = 'USE PROPER CAPITALIZATION';
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
		//ITCS
		else if (QKey == 'KJ') {
			Question = import.meta.env.VITE_IT_05_Q;
			showModal = true;
		} else if (QKey == 'MK') {
			Question = import.meta.env.VITE_CS_15_Q;
			showModal = true;
		} else if (QKey == 'MMP') {
			Question = import.meta.env.VITE_IT_MP_Q;
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

	const answerCheck = () => {
		//TM
		if (QKey == 'KC' && Answer == import.meta.env.VITE_TM_KC_A1 || QKey == 'KC' && Answer == import.meta.env.VITE_TM_KC_A2) {
			localStorage.setItem('letterKey', 'TM-KC');
			goto(base + '/TM/TM-KC');
		} else if (QKey == 'MA' && Answer == import.meta.env.VITE_TM_12_A) {
			localStorage.setItem('letterKey', 'TM-12');
			goto(base + '/TM/TM-12');
		} else if (QKey == 'J' && Answer == import.meta.env.VITE_TM_10_A) {
			localStorage.setItem('letterKey', 'TM-10');
			goto(base + '/TM/TM-10');
		} else if (QKey == 'E' && Answer == import.meta.env.VITE_TM_26_A) {
			localStorage.setItem('letterKey', 'TM-26');
			goto(base + '/TM/TM-26');
		} 
		//ITCS
		else if (QKey == 'KJ' && Answer == import.meta.env.VITE_IT_05_A1 || QKey == 'KJ' && Answer == import.meta.env.VITE_IT_05_A2) {
			localStorage.setItem('letterKey', 'IT-05');
			goto(base + '/IT/IT-05');
		} else if (QKey == 'MK' && Answer == import.meta.env.VITE_CS_15_A) {
			localStorage.setItem('letterKey', 'CS-15');
			goto(base + '/CS/CS-15');
		} else if (QKey == 'MMP' && Answer == import.meta.env.VITE_IT_MP_A) {
			localStorage.setItem('letterKey', 'IT-2024-MP');
			goto(base + '/IT/IT-MP');
		}
		//NTS
		else if (QKey == 'Q' && Answer == import.meta.env.VITE_GA_15_A) {
			localStorage.setItem('letterKey', 'GA-15');
			goto(base + '/NTS/GA-15');
		} else if (QKey == 'SL-A' && Answer == import.meta.env.VITE_SL_24_A1 || QKey == 'SL-A' && Answer == import.meta.env.VITE_SL_24_A2) {
			localStorage.setItem('letterKey', 'SL-24');
			goto(base + '/NTS/SL-24');
		} else if (QKey == 'SN-A' && Answer == import.meta.env.VITE_SN_19_A1 || QKey == 'SN-A' && Answer == import.meta.env.VITE_SN_19_A2) {
			localStorage.setItem('letterKey', 'SN-19');
			goto(base + '/NTS/SN-19');
		}
		else
		{
			pHolder = 'Try again';
		}
		Answer = '';
	};
</script>
<!-- //!commented parts are title head and year and letterCode -->
<title>Letter Storage System</title>
<h1 class="text-3xl text-center m-9 mb-4">Welcome</h1>
<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-img-redundant-alt -->
<div>
	<!-- <h1 class="text-lg m-2 text-center">Please select your Year/Course or work in the list below</h1> -->
	<h1 class="text-lg m-2 text-center">Please click on the letter below</h1>
	<!-- TM -->
	<div class="gridName text-center">
		<!-- <h1 class="text-2xl mb-2">Tourism Management</h1>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'KC')}>
			<p class="text-xl">
				3rd year | TM-KC
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5 " on:click={() => (QKey = 'MA')}>
			<p class="text-xl">
				1st year | TM-12
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'J')}>
			<p class="text-xl">
				1st year | TM-10
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'E')}>
			<p class="text-xl">
				1st year | TM-26
			</p>
		</div> -->
	</div>
	<!-- IT/CS -->
	<div class="gridName text-center">
		<!-- <h1 class="text-2xl mb-2">ICT</h1> -->
		<h1 class="text-2xl mb-2">Graduation letters</h1>
		<!-- <div class="gridDesc flex overflow-hidden mb-5 justify-center" on:click={() => (QKey = 'KJ')}>
			<p class="text-xl">
				3rd year | IT | IT-05
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5 text-center" on:click={() => (QKey = 'MK')}>
			<p class="text-xl">
				2nd year | CS | CS-15
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5 text-center" on:click={() => (QKey = 'MMP')}>
			<p class="text-xl">
				4th year | IT | IT-2024-MP
			</p>
		</div> -->
		<div class="gridDesc flex overflow-hidden mb-5 text-center" on:click={() => (goto(base + '/STI'))}>
			<p class="text-xl">
				Final letter
			</p>
		</div>
		<!-- <div class="gridDesc flex overflow-hidden mb-5 text-center" on:click={() => (goto(base + '/FF'))}>
			<p class="text-xl">
				Family and friends
			</p>
		</div> -->
	</div>
	<!-- NTS -->
	<div class="gridName text-center">
		<!-- <h1 class="text-2xl mb-2">Non-Teaching Staff</h1>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'Q')}>
			<p class="text-xl">
				Guidance Associate | GA-15
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'SL-A')}>
			<p class="text-xl">
				School Librarian | SL-24
			</p>
		</div>
		<div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'SN-A')}>
			<p class="text-xl">
				School Nurse | SN-19
			</p>
		</div> -->
	</div>
</div>
<Modal bind:showModal>
	<h2 slot="header" class="text-2xl text-center">Passphrase</h2>
	<p class="text-base text-center textWarning">{pHolder}</p>
	<p class="text-base text-center">{Question}</p>
	<form on:submit|preventDefault={answerCheck} class="text-center">
		<input type="text" class="border-b-2 rounded-sm m-2" placeholder="Answer" bind:value={Answer} />
		<hr />
		<button
			class="text-white inline-flex w-full justify-center font-medium text-sm px-5 py-2.5 text-center"
			>Submit</button
		>
	</form>
</Modal>

<style lang="postcss">
	.textWarning {
		color: #991b1b;
	}
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