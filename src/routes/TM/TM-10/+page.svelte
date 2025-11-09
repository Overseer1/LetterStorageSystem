<script>
	// @ts-nocheck
	import cartas from '../letterHolderTM.json'
	// import MJ from '$lib/assets/TM/J.jpg?url';
	// import MJB from '$lib/assets/TM/J1.webp?url';
	// import MJ2 from '$lib/assets/TM/J2.jpg?url';
	// import MJ3 from '$lib/assets/TM/J3.jpg?url';
	// import MJ4 from '$lib/assets/TM/J4.jpg?url';
	// import MJ5 from '$lib/assets/TM/J5.jpg?url';
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
	const graduationPlaceholder = cartas.TM10.Graduation.Footer.replace(/\n/g, '<br />');
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
	<!-- <img src={MJ} alt="N/A" class="object-cover mt-5 h-[250px] w-[450px] rounded-lg imgHead" /> -->
</header>
<hr />
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">Please select the letter that you want to read.</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<!-- img={MJ3} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
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
		<!-- img={MJ4} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
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
		<!-- img={MJ2} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
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
		<!-- img={MJ5} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
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
					<!-- <img src={MJB} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" /> -->
				</div>
				<article class="m-5">
					Hai Jovy, HAPPY 20TH BIRTHDAY SAYO MI ANAKISSS!!! or HAPPY 20TH BIRTHDAY SAYO MY FOUNDING
					MOTHER!!! Sorry kung eto lang regalo ko, yung picture naman na naka layout is gawa ko
					naman kaya ayan lang muna ha? Anw, dahil ikaw ay 20 na, dapat maging maayos ang decisions
					and/or choices mo sa life and of course, nandito lang kami for you. Tandaan mo palagi yon
					ha? Nandito lang ako, si Kat Kat, si Asli, si Marielle, at kung sino pa para supportahan,
					samahan, tulungan, at pakinggan ka. Oki? Ano pa ba, well namimiss ko na random photoshoots
					natin. Aminin natin na mas madami photoshoots ni Kat Kat at ni Asli, pero kulang pics mo
					dito aba. Dapat madami to eh, so dapat makapag photoshoot tayo soon. Feel ko need mo
					malaman to kahit alam na alam mo na to, so eto, mahal na mahal ka namin, as in. Kahit alam
					mo na yan, sabihin mo na lang na reminder lang yon. So ayun. Sana nasa mabuting kalagayan
					ka ngayon and mag ingat ka palagi ha? Miss na miss ka na namin or should I say, MISS NA
					MISS NA KITA!!! Sana talaga magkita tayo soon. Of course, sorry kung minsan
					napapaoverthink kita and sa kung ano pang bad things. I'm really sorry anak. I wish you
					all the best girl, do your best lang ha? Proud na proud ako sayo kahit malayo ako sayo.
					Uulitin ko, nandito lang ako/kami for you ha? I love you so fucking much Jovy, Alam mo
					yon. I'm so thankful for you mi hija. Ikaw nag link sa amin ni Kat Kat at Asli, naging
					founding mother (wao) ng 2nd circle ko, and syempre, naging kaibigan kita, tas malapit pa.
					It's beautiful. Nakakamiss ka sobra. Baka maiyak pa tayong dalawa pag nagkita tayo ulit.
					Do me a favor, grumaduate ka ng may Latin Honors. Si Kat Kat ang unang kaibigan natin na
					magiging Cum Laude, dapat ikaw din at yung iba ay Cum Laude. Okay lang kung hindi, at
					least ginawa niyo best niyo. I know that and I'm proud of you for doing your best. See u
					soonest, God bless you, and to more memories with you!!!
				</article>
				<footer class="m-5 text-end">
					From your school father, photographer, and close friend, <br />
					Hanz
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
			<h2 slot="letterType" class="text-white text-xl cheatline text-center select-none">Graduation letter</h2>
			<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: 2026/2027 | Letter written: 2027 
			</p>
			<div class="text-[#f5f3f3]">
				<!-- //* insert img here (preferrably grad pic) -->
				<article class="m-5">
					Jovy M. Margate | Batch 2027 <br />
					Bachelor of Science in Tourism Management <br />
				</article>
				<article class="m-5">
					
				</article>
				<footer class="m-5 text-end">
					From your school father, photographer, and close friend, <br />
					Hanz
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
