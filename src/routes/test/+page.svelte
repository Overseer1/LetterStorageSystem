<script>
	import { base } from '$app/paths';
	// Assuming you will create a custom Modal component that does not rely on flowbite-svelte
	import Modal from '../components/Modal.svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	// Removed Flowbite components

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
	}
	onMount(async () => {
		let hasItem = localStorage.getItem('letterKey') !== null;
		if (hasItem) {
			localStorage.removeItem('letterKey');
		}
	});

	$: {
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

<div class="min-h-screen bg-gray-900 text-gray-200 font-sans p-4 sm:p-6 lg:p-8">
	<h1 class="text-4xl sm:text-5xl font-extrabold text-center mt-8 mb-4 text-blue-400">Welcome</h1>
	<p class="text-lg text-center mb-6">
		Please select your Year/Course or work in the cards below
	</p>
	<p class="text-lg text-center mb-8">
		Note: <span class="text-yellow-400 font-semibold">Yellow</span> = under development |
		<span class="text-emerald-400 font-semibold">Light Green</span> = New letters
	</p>

	<h2 class="text-3xl font-bold text-center my-8 py-3 bg-gray-800 rounded-lg shadow-inner">Tourism Management</h2>
	<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-5 gap-6 mb-10">
		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-emerald-400">TM-KC-2025</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">Alumnus Batch 2025, Cum Laude</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'KC')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">TM-12</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">3rd year</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'MA')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">TM-10</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">2nd year</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'J')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">TM-26</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">3rd year</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'E')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">TM-F-12</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">Former faculty</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'LJ')}
			>
				Open
			</button>
		</div>
	</div>

	<h2 class="text-3xl font-bold text-center my-8 py-3 bg-gray-800 rounded-lg shadow-inner">ICT</h2>
	<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-5 gap-6 mb-10">
		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-emerald-400">IT-05-2025</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">IT Alumnus Batch 2025</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'KJ')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">CS-15</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">CS 3rd year</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'MK')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">IT-2024-12</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">IT Alumnus Batch 2024</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'MMP')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">IT-F-26</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">IT Faculty, IT Alumnus Batch 2024</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'CF')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-yellow-400">IT-F-20</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">Former IT Faculty, IT Alumnus Batch 2023</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'JB')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">IT-2020-2024-05</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">ITM Batch 2020, IT Alumnus Batch 2024</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'SA/WD')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-yellow-400">ITM20-IT/E24-IT25</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">IC/IT/E Alumni (Placeholder only)</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'ICITE')}
			>
				Open
			</button>
		</div>
	</div>

	<h2 class="text-3xl font-bold text-center my-8 py-3 bg-gray-800 rounded-lg shadow-inner">Non-Teaching Staff</h2>
	<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 mb-10">
		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">GA-15-2024</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">Former Guidance Associate</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'Q')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">SL-24</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">School Librarian</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'SL-A')}
			>
				Open
			</button>
		</div>

		<div
			class="relative bg-gray-800 rounded-xl shadow-md p-6 flex flex-col items-start justify-between
			transition-all duration-300 ease-in-out transform hover:scale-[1.02] hover:shadow-lg
			border border-gray-700 hover:border-blue-500"
		>
			<h5 class="text-2xl font-bold mb-2 text-gray-200">SN-19-2025</h5>
			<p class="text-base text-gray-300 mb-4 flex-grow">Former School Nurse</p>
			<button
				class="w-full bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
				on:click={() => (QKey = 'SN-A')}
			>
				Open
			</button>
		</div>
	</div>
</div>

{#if QKey}
	<Modal bind:showModal>
		<h2 slot="header" class="text-3xl font-bold text-center pb-4 mb-4 border-b border-gray-700 text-blue-400">Passphrase</h2>
		<p class="text-base text-center text-red-500 mb-2">{pHolder}</p>
		<p class="text-lg text-center text-gray-200 mb-4">{Question}</p>
		<form on:submit|preventDefault={answerCheck} class="text-center flex flex-col items-center">
			<input
				type="text"
				class="w-full max-w-sm px-4 py-2 mb-4 rounded-md border border-gray-600 bg-gray-700 text-white
				focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500 placeholder-gray-400"
				placeholder="Answer"
				bind:value={Answer}
			/>
			<button
				type="submit"
				class="w-full max-w-sm bg-blue-600 text-white py-2 rounded-md font-semibold
				hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-gray-900
				transition-colors duration-200 ease-in-out"
			>
				Submit
			</button>
		</form>
	</Modal>
{/if}

<style lang="postcss">
	/* The global style for html has been moved to the main div classes for better encapsulation.
       The .cheatline class is no longer needed as its styling is handled by Tailwind utilities directly on the h2 elements. */
	/* No custom CSS needed here as all styles are handled by Tailwind classes */
</style>