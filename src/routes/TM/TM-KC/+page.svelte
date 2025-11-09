<script>
	// @ts-nocheck
	import cartas from '../letterHolderTM.json'
	// import CKC from '$lib/assets/TM/KC.jpg?url';
	// import CKC1 from '$lib/assets/TM/KC1.jpg?url';
	// import CKC2 from '$lib/assets/TM/KC2.jpg?url';
	// import CKC3 from '$lib/assets/TM/KC3.jpg?url'; //unused
	// import CKC4 from '$lib/assets/TM/KC4.jpg?url';
	// import CKC5 from '$lib/assets/TM/KC5.jpg?url'; //unused
	// import CKC6 from '$lib/assets/TM/KC6.jpg?url';
	// import CKC7 from '$lib/assets/TM/KC7.jpg?url'; //unused
	// import CKC8 from '$lib/assets/TM/KC8.jpg?url';
	// import CKC9 from '$lib/assets/TM/KC9.jpg?url';
	// import CKC10 from '$lib/assets/TM/KC10.webp?url';
	// import CKC11 from '$lib/assets/TM/KC11.jpg?url';
	// import CKC12 from '$lib/assets/TM/KC12.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle, Spinner } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let showModal = false;
	let letterContent = '';
	let userCheck = '';
	function letterShow(contentSelect) {
		letterContent = contentSelect;
		showModal = true;
	}
	const gratitudeFooter = cartas.TMKC.Gratitude.Footer.replace(/\n/g, '<br />');
	const birthdayFooter = cartas.TMKC.Birthday.Footer.replace(/\n/g, '<br />');
	const graduationHeader = cartas.TMKC.Graduation.Header.replace(/\n/g, '<br />');
	const graduationFooter = cartas.TMKC.Graduation.Footer.replace(/\n/g, '<br />');
	const sendEmail = (/** @type {{ target: string | HTMLFormElement; }} */ e) => {
		emailjs
			.sendForm(
				import.meta.env.VITE_EmailJS_ServiceID,
				import.meta.env.VITE_EmailJS_TemplateIDFF,
				e.target,
				{
					publicKey: import.meta.env.VITE_EmailJS_PublicKey
				}
			)
			.then(
				() => {
					console.log('SUCCESS!');
					alert('Message sent');
				},
				(error) => {
					console.log('FAILED...', error.text);
				}
			);
	};
	$: {
		// Page non-accessible to others. Only to the developer.
		let hasItem;
		let valueCheck;
		onMount(async () => {
			hasItem = localStorage.getItem('letterKey') !== null;
			valueCheck = localStorage.getItem('letterKey');
			// if (hasItem && valueCheck == import.meta.env.VITE_TM_KC_T) {
			// } else {
			// 	goto(base + '/');
			// }
			if (hasItem && valueCheck == import.meta.env.VITE_SiteKey) {
			} else {
				goto(base + '/');
			}
			return userCheck = localStorage.getItem('letterKey');
		});
	}
</script>

{#if userCheck == import.meta.env.VITE_TM_KC_T}
<title>Henlo, Kat Kattttt</title>
<div class="text-center m-5">Welcome, Cabrera, K. C.</div>
{:else if userCheck == import.meta.env.VITE_SiteKey}
<title>Hello Developer.</title>
<div class="text-center m-5">Welcome, Lizaso, H. This is now hidden from her.</div>
{/if}
<div class="cheatline text-center">Page updated: July 10, 2025</div>
<header class="mb-5 flex justify-center">
	<!-- <img src={CKC9} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" /> -->
</header>
<hr />
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">Please select the letter that you want to read.</p>
</header>

<div class="flex justify-center max-sm:block">
	<div class="overflow-hidden mb-5 flex justify-center mx-5">
		<!-- img={CKC} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Gratitude letter</h5>
			<p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
			<Button
				class="bg-bgPurp border border-[#6d28d9] hover:bg-[#6d28d9]"
				on:click={() => letterShow('Gratitude')}
			>
				Open letter
			</Button>
		</Card>
	</div>

	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<!-- img={CKC4} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">To my 2nd circle</h5>
			<p class="mb-3 font-normal leading-tight">Access to cartas secreta.</p>
			<Button
				class="bg-bgPurp border border-[#6d28d9] hover:bg-[#6d28d9]"
				on:click={() => letterShow('Reminder')}
			>
				Open letter
			</Button>
		</Card>
	</div>

	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<!-- img={CKC8} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Birthday letter</h5>
			<p class="mb-3 font-normal leading-tight">
				Happy 22nd birthday mi hermana, bff, and model!!!
			</p>
			<Button
				class="bg-bgPurp border border-[#6d28d9] hover:bg-[#6d28d9]"
				on:click={() => letterShow('Birthday')}
			>
				Open letter
			</Button>
		</Card>
	</div>

	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<!-- img={CKC11} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Graduation letter</h5>
			<p class="mb-3 font-normal leading-tight">Congratulations mi hermana!</p>
			<Button
				class="bg-bgPurp border border-[#6d28d9] hover:bg-[#6d28d9]"
				on:click={() => letterShow('Graduation')}
			>
				Open letter
			</Button>
		</Card>
	</div>
	{#if letterContent === 'Gratitude'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
			<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: June 10, 2024 | Letter written: June 11, 2024 | Letter updated: July 16,
				2024
			</h3>
			<div class="text-[#f5f3f3]">
				<!-- //* you may add carousel or images in between -->
				<article class="m-5">
					{cartas.TMKC.Gratitude.Section1}
				</article>
				<article class="m-5">
					{cartas.TMKC.Gratitude.Section2} 
				</article>
				<article class="m-5">
					{cartas.TMKC.Gratitude.Section3}
				</article>
				<article class="m-5">
					{cartas.TMKC.Gratitude.Section4}
				</article>
				<footer class="m-5 text-end">
					{@html gratitudeFooter}
				</footer>
				<article class="m-5">
					{cartas.TMKC.Gratitude.PostScript}
				</article>
			</div>
		</Modal>
	{:else if letterContent === 'Reminder'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center">To my 2nd circle</h2>
			<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: October 9, 2024
			</h3>
			<div class="text-[#f5f3f3]">
				<article class="m-5">
					Please access this page, <button
						class="cursor-pointer underline"
						on:click={() => goto(base + '/ToTheOnes')}>to my second circle.</button
					>
				</article>
				<footer class="m-5 text-end">From the developer.</footer>
			</div>
		</Modal>
	{:else if letterContent === 'Birthday'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center">Birthday letter</h2>
			<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: December 1, 2024 | Letter written: December 8, 2024
			</h3>
			<div class="flex justify-center">
				<!-- <img src={CKC10} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" /> -->
			</div>
			<div class="text-[#f5f3f3]">
				<article class="m-5">
					{cartas.TMKC.Birthday.Section1}
				</article>
				<article class="m-5">
					{cartas.TMKC.Birthday.Section2}
				</article>
				<article class="m-5">
					{cartas.TMKC.Birthday.Section3}
				</article>
				<article class="m-5">
					{cartas.TMKC.Birthday.Section4}
				</article>
				<footer class="m-5 text-end">
					{@html birthdayFooter}
				</footer>
				<article class="m-5">
					{cartas.TMKC.Birthday.PostScript}
				</article>
			</div>
		</Modal>
	{:else if letterContent === 'Graduation'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center">
				Graduation letter 
			</h2>
			<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Draft Started: February 27, 2025 | Letter finished: July 9, 2025 | Letter written: July 10, 2025
			</h3>
			<div class="flex justify-center">
				<!-- <img src={CKC12} alt="N/A" class="object-cover mt-5 h-[250px] w-[250px] rounded-lg" /> -->
			</div>
			<div class="text-[#f5f3f3]">
				<article class="m-5">
					{@html graduationHeader}
				</article>
				<article class="m-5">
					{cartas.TMKC.Graduation.Section1}
				</article>
				<article class="m-5">
					{cartas.TMKC.Graduation.Section2}
				</article>
				<article class="m-5">
					{cartas.TMKC.Graduation.Section3}
				</article>
				<footer class="m-5 text-end">
					{@html graduationFooter}
				</footer>
			</div>
		</Modal>
	{/if}
</div>

<hr />

<div class="text-center mt-5">
	If you want, you may leave a message to the developer. <br /> You may change your name in the text
	box below.
</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input
			type="text"
			placeholder="Name"
			name="from_name"
			class=" border rounded-lg text-black m-4 p-1 inputColor"
			value="Katrina/Kat Kat"
			required
		/>
	</div>
	<div class="flex justify-center">
		<textarea name="message" placeholder="Message" class="border rounded-lg inputColor p-1" required
		/>
		<button
			type="submit"
			value="Send"
			class="border rounded-lg p-2 mt-auto mb-auto ml-5 buttonChange">send</button
		>
	</div>
</form>
<button class="m-10 float-end border rounded-lg p-2" on:click={() => goto(base + '/')}>
	<Icon icon="ep:back" style="color: #dddddd" />
</button>

<style lang="postcss">
	.cheatline {
		background-color: #6d28d9;
		color: #f5f3f3;
	}
	.inputColor {
		color: #313131;
	}
	:global(html) {
		background-color: theme(colors.bgPurp);
		color: #f5f3f3;
	}
	@media screen and (max-width: 700px) {
		img {
			width: 77%;
		}
		.buttonChange {
			margin-right: 12px;
		}
		/* partial implementation only */
		/* header
		{
			display: block;
			height: auto;
			width: auto;
			margin-left:120px;
		} */
	}
	textarea {
		width: 500px;
		height: 200px;
	}
	@media screen and (max-width: 500px) {
		textarea {
			width: 500px;
			height: 200px;
			margin: 15px;
		}
	}
</style>
