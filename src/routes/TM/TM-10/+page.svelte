<script>
	// @ts-nocheck
	import cartas from '../letterHolderTM.json'
	import MJ from '$lib/assets/TM/J0.jpg?url';
	import MJB from '$lib/assets/TM/J1B.webp?url';
	import MJ2 from '$lib/assets/TM/J02.jpg?url';
	import MJ3 from '$lib/assets/TM/J03.jpg?url';
	import MJ4 from '$lib/assets/TM/J04.jpg?url';
	import MJ5 from '$lib/assets/TM/J5.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let showModal = false;
	let letterContent = '';
	const gratitudeFooter = cartas.TM10.Gratitude.Footer.replace(/\n/g, '<br />');
	const birthdayFooter = cartas.TM10.Birthday.Footer.replace(/\n/g, '<br />');
	const graduationHeader = cartas.TM10.Graduation.Header.replace(/\n/g, '<br />');
	const graduationFooter = cartas.TM10.Graduation.Footer.replace(/\n/g, '<br />');
	function letterShow(contentSelect) {
		letterContent = contentSelect;
		showModal = true;
	}
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
		let hasItem;
		let valueCheck;
		onMount(async () => {
			hasItem = localStorage.getItem('letterKey') !== null;
			valueCheck = localStorage.getItem('letterKey');
			// Conditional logic based on hasItem
			if (hasItem && valueCheck == import.meta.env.VITE_TM_10_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>

<title>Hello mi bebeeee</title>
<div class="text-center m-5">Welcome, Margate, J.</div>
<div class="cheatline text-center">Page updated: November 3, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={MJ} alt="N/A" class="object-cover mt-5 h-[250px] w-[450px] rounded-lg imgHead" />
</header>
<hr />
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">Please select the letter that you want to read.</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MJ3} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Gratitude letter</h5>
			<p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
			<Button
				class="bg-bgRoseGold border border-[#b76e79] hover:bg-[#b76e79]"
				on:click={() => letterShow('Gratitude')}
			>
				Open letter
			</Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MJ4} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">To my 2nd circle</h5>
			<p class="mb-3 font-normal leading-tight">Access to cartas secreta.</p>
			<Button
				class="bg-bgRoseGold border border-[#b76e79] hover:bg-[#b76e79]"
				on:click={() => letterShow('Reminder')}
			>
				Open letter
			</Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MJ2} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Birthday letter</h5>
			<p class="mb-3 font-normal leading-tight">
				Happy 20th birthday mi hija, hermana, bff, and model!!!
			</p>
			<Button
				class="bg-bgRoseGold border border-[#b76e79] hover:bg-[#b76e79]"
				on:click={() => letterShow('Birthday')}
			>
				Open letter
			</Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MJ5} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Being drafted</h5>
			<p class="mb-3 font-normal leading-tight">
				Draft is hidden as per my decision.
			</p>
			<Button
				class="bg-bgRoseGold border border-[#b76e79] hover:bg-[#b76e79]"
				on:click={() => letterShow('Graduation')}
			>
				Open letter
			</Button>
		</Card>
	</div>
	{#if letterContent === 'Gratitude'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
			<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: June 13, 2024 | Letter written: June 14, 2024 | Letter updated: July 04,
				2024
			</p>
			<div class="text-[#f5f3f3]">
				<!-- //* you may add carousel or images in between -->
				<article class="m-5">
					{cartas.TM10.Gratitude.Section1}
				</article>
				<article class="m-5">
					{cartas.TM10.Gratitude.Section2}
				</article>
				<article class="m-5">
					{cartas.TM10.Gratitude.Section3}
				</article>
				<footer class="m-5 text-end">
					{@html gratitudeFooter}
				</footer>
				<article class="m-5">
					{cartas.TM10.Gratitude.PostScript}
				</article>
			</div>
		</Modal>
	{:else if letterContent === 'Birthday'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center">Birthday letter</h2>
			<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: October 15, 2024
			</p>
			<div class="text-[#f5f3f3]">
				<div class="flex justify-center">
					<img src={MJB} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" />
				</div>
				<article class="m-5">
					{cartas.TM10.Birthday.Section1}
				</article>
				<footer class="m-5 text-end">
					{@html birthdayFooter}
				</footer>
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
	{:else if letterContent === 'Graduation'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center select-none blur-md">Graduation letter</h2>
			<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: 2026/2027 | Letter written: 2027 
			</p>
			<div class="text-[#f5f3f3]">
				<!-- //* insert img here (preferably grad pic) -->
				<article class="m-5">
					{@html graduationHeader}
				</article>
				<article class="m-5">
					{cartas.TM10.Graduation.placeholder}
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
			value="Jovy/Anakis"
			required
		/>
	</div>
	<div class="flex justify-center">
		<textarea name="message" placeholder="Message" class="border rounded-lg inputColor p-1" required
		></textarea>
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
		background-color: #b76e79;
		color: #f5f3f3;
	}
	:global(html) {
		background-color: theme(colors.bgRoseGold);
		color: #dddddd;
	}
	@media screen and (max-width: 600px) {
		.imgHead {
			width: 77%;
		}
		.buttonChange {
			margin-right: 12px;
		}
	}
	.inputColor {
		color: #313131;
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
