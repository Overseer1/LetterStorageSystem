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
		if (
			(QKey == 'KC' && Answer == import.meta.env.VITE_TM_KC_A1) ||
			(QKey == 'KC' && Answer == import.meta.env.VITE_TM_KC_A2)
		) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_KC_T);
			goto(base + '/TM/TM-KC');
		} else if (
			(QKey == 'MA' && Answer == import.meta.env.VITE_TM_12_A1) ||
			(QKey == 'MA' && Answer == import.meta.env.VITE_TM_12_A2)
		) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_12_T);
			goto(base + '/TM/TM-12');
		} else if (QKey == 'J' && Answer == import.meta.env.VITE_TM_10_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_10_T);
			goto(base + '/TM/TM-10');
		} else if (QKey == 'E' && Answer == import.meta.env.VITE_TM_26_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_26_T);
			goto(base + '/TM/TM-26');
		} else if (
			(QKey == 'LJ' && Answer == import.meta.env.VITE_TM_F_12_A1) ||
			(QKey == 'LJ' && Answer == import.meta.env.VITE_TM_F_12_A2) ||
			(QKey == 'LJ' && Answer == import.meta.env.VITE_TM_F_12_A3)
		) {
			localStorage.setItem('letterKey', import.meta.env.VITE_TM_F_12_T);
			goto(base + '/TM/TM-F-12');
		}
		//ITCS
		else if (
			(QKey == 'KJ' && Answer == import.meta.env.VITE_IT_05_A1) ||
			(QKey == 'KJ' && Answer == import.meta.env.VITE_IT_05_A2)
		) {
			localStorage.setItem('letterKey', import.meta.env.VITE_IT_05_T);
			goto(base + '/IT/IT-05');
		} else if (QKey == 'MK' && Answer == import.meta.env.VITE_CS_15_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_CS_15_T);
			goto(base + '/CS/CS-15');
		} else if (QKey == 'MMP' && Answer == import.meta.env.VITE_IT_12_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_IT_12_T);
			goto(base + '/IT/IT-12');
		} else if (
			(QKey == 'CF' && Answer == import.meta.env.VITE_IT_26_A1) ||
			(QKey == 'CF' && Answer == import.meta.env.VITE_IT_26_A2)
		) {
			localStorage.setItem('letterKey', import.meta.env.VITE_IT_26_T);
			goto(base + '/IT/IT-F-26');
		} else if (QKey == 'SA/WD' && Answer == import.meta.env.VITE_DevPass) {
			localStorage.setItem('letterKey', import.meta.env.VITE_SiteKey);
			goto(base + '/IT/IT-00');
		} else if (
			(QKey == 'JB' && Answer == import.meta.env.VITE_IT_20_A1) ||
			(QKey == 'JB' && Answer == import.meta.env.VITE_IT_20_A2)
		) {
			localStorage.setItem('letterKey', import.meta.env.VITE_IT_20_T);
			goto(base + '/IT/IT-F-20');
		} else if (QKey == 'ICITE' && Answer == import.meta.env.VITE_DevPass) {
			localStorage.setItem('letterKey', import.meta.env.VITE_SiteKey);
			goto(base + '/ToTheOnes');
		}
		//NTS
		else if (QKey == 'Q' && Answer == import.meta.env.VITE_GA_15_A) {
			localStorage.setItem('letterKey', import.meta.env.VITE_GA_15_T);
			goto(base + '/NTS/GA-15');
		} else if (
			(QKey == 'SL-A' && Answer == import.meta.env.VITE_SL_24_A1) ||
			(QKey == 'SL-A' && Answer == import.meta.env.VITE_SL_24_A2)
		) {
			localStorage.setItem('letterKey', import.meta.env.VITE_SL_24_T);
			goto(base + '/NTS/SL-24');
		} else if (
			(QKey == 'SN-A' && Answer == import.meta.env.VITE_SN_19_A1) ||
			(QKey == 'SN-A' && Answer == import.meta.env.VITE_SN_19_A2)
		) {
			localStorage.setItem('letterKey', import.meta.env.VITE_SN_19_T);
			goto(base + '/NTS/SN-19');
		} else if (Answer == '') {
			pHolder = 'Preferably with an answer.';
		} else {
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
		} else if (QKey == 'SA/WD') {
			Question = 'Your password please.';
			showModal = true;
		} else if (QKey == 'ICITE') {
			//replace with key from env
			Question = 'Your password please.';
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
	<h1 class="text-lg m-2 text-center">Please select your Year/Course or work in the cards below</h1>
	<h1 class="text-lg m-2 text-center">
		Note: <span class="text-[#eed202]">Yellow</span> = under development |
		<span class="text-green-400">Light Green</span> = New letters
	</h1>
	<!-- //* Tourism Management  -->
	<h1 class="text-2xl text-center cheatline my-5">Tourism Management</h1>
	<div class="flex justify-center max-sm:block">
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight text-green-400">TM-KC-2025</h5>
					<p class="mb-3 font-normal leading-tight">Alumnus Batch 2025, Cum Laude</p>
				<Button
				class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
				on:click={() => (QKey = 'KC')}
				>
				Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">TM-12</h5>
				<p class="mb-3 font-normal leading-tight">3rd year</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'MA')}
				>
					Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">TM-10</h5>
				<p class="mb-3 font-normal leading-tight">2nd year</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'J')}
				>
					Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">TM-26</h5>
				<p class="mb-3 font-normal leading-tight">3rd year</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'E')}
				>
					Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">TM-F-12</h5>
				<p class="mb-3 font-normal leading-tight">Former faculty</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'LJ')}
				>
					Open
				</Button>
			</Card>
		</div>
	</div>
	<hr />
	<!-- //* InfoTech/ComSci -->
	<h1 class="text-2xl text-center cheatline my-5">ICT</h1>
	<div class="flex justify-center max-sm:block">
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight text-green-400">IT-05-2025</h5>
				<p class="mb-3 font-normal leading-tight">IT Alumnus Batch 2025</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'KJ')}
				>
					Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">CS-15</h5>
				<p class="mb-3 font-normal leading-tight">CS 3rd year</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'MK')}
				>
					Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">IT-2024-12</h5>
				<p class="mb-3 font-normal leading-tight">IT Alumnus Batch 2024</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'MMP')}
				>
					Open
				</Button>
			</Card>
		</div>
	</div>
	<!-- //! Remove divider once it fits all 6 cards in one div flex -->
	<div class="flex justify-center max-sm:block">
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">IT-F-26</h5>
				<p class="mb-3 font-normal leading-tight">IT Faculty, IT Alumnus Batch 2024</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'CF')}
				>
					Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight text-[#eed202]">IT-F-20</h5>
				<p class="mb-3 font-normal leading-tight">Former IT Faculty, IT Alumnus Batch 2023</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'JB')}
				>
					Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">IT-2020-2024-05</h5>
				<p class="mb-3 font-normal leading-tight">ITM Batch 2020, IT Alumnus Batch 2024</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'SA/WD')}
				>
					Open
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight text-[#eed202]">ITM20-IT/E24-IT25</h5>
				<p class="mb-3 font-normal leading-tight">IC/IT/E Alumni (Placeholder only)</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'ICITE')}
				>
					Open
				</Button>
			</Card>
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
	<hr />
	<!-- //* Non-Teaching Staff -->
	<h1 class="text-2xl text-center cheatline my-5">Non-Teaching Staff</h1>
	<div class="flex justify-center max-sm:block">
		<!-- <div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'Q')}>
			<p class="text-xl">Former Guidance Associate | GA-15-2024</p>
		</div> -->
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">GA-15-2024</h5>
				<p class="mb-3 font-normal leading-tight">Former Guidance Associate</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'Q')}
				>
					Open
				</Button>
			</Card>
		</div>
		<!-- <div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'SL-A')}>
			<p class="text-xl">School Librarian | SL-24</p>
		</div> -->
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">SL-24</h5>
				<p class="mb-3 font-normal leading-tight">School Librarian</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'SL-A')}
				>
					Open
				</Button>
			</Card>
		</div>
		<!-- <div class="gridDesc flex overflow-hidden mb-5" on:click={() => (QKey = 'SN-A')}>
			<p class="text-xl">Former School Nurse | SN-19-2025</p>
		</div> -->
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card reverse={false} class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight">SN-19-2025</h5>
				<p class="mb-3 font-normal leading-tight">Former School Nurse</p>
				<Button
					class="bg-bgBlack border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]"
					on:click={() => (QKey = 'SN-A')}
				>
					Open
				</Button>
			</Card>
		</div>
	</div>
</div>
{#if QKey}
	<Modal bind:showModal>
		<h2 slot="header" class="text-2xl text-center border-b-2 border-bgBlack">Passphrase</h2>
		<p class="text-base text-center text-[#991b1b]">{pHolder}</p>
		<p class="text-base text-center">{Question}</p>
		<form on:submit|preventDefault={answerCheck} class="text-center">
			<input
				type="text"
				class="border-b-2 rounded-sm my-2"
				placeholder="Answer"
				bind:value={Answer}
			/>
			<hr />
			<button
				class="inline-flex w-full justify-center border-t-2 border-b-2 border-bgBlack font-medium text-sm px-5 py-2.5 text-center"
			>
				Submit
			</button>
		</form>
	</Modal>
{/if}

<style lang="postcss">
	.cheatline {
		background-color: #dddddd;
		color: #313131;
	}
	:global(html) {
		background-color: theme(colors.bgBlack);
		color: #dddddd;
	}
</style>
