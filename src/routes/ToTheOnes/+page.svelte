<script>
	// @ts-nocheck
	import Modal from '../components/Modal.svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import { page } from '$app/stores';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	const circleSelection = ['TA/1C', 'TS/2C'];
	const tokenFinder = [import.meta.env.VITE_TM_KC_T, import.meta.env.VITE_TM_12_T, import.meta.env.VITE_TM_10_T, import.meta.env.VITE_TM_26_T, import.meta.env.VITE_IT_05_T, import.meta.env.VITE_CS_15_T, import.meta.env.VITE_SiteKey];
	let CircleType, UserName, ShowLetter, Question, Passkey, firstKey, addKeys;
	let Attempts = 5;
	let showModal = false;
	let pHolder = 'Use proper capitalization please.';
	let showAttempts = 'Attempts: ' + Attempts;
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
	const verifier = () => {
		// firstCircle/Alumnis
		if (CircleType == circleSelection[0]) {
			if (Passkey == ' ') {
				Attempts--;
				showAttempts = 'Attempts: ' + Attempts;
				pHolder = "Adding just a space ain't gonna work, you understand?";
				Passkey = null;
			} else if (import.meta.env.VITE_FC_A1.includes(Passkey) || import.meta.env.VITE_FC_A1_N.includes(Passkey)) {
				UserName = 'Asistio, Z. L.';
				ShowLetter = 'firstCircle';
			} else if (import.meta.env.VITE_FC_A2.includes(Passkey) || import.meta.env.VITE_FC_A2_N.includes(Passkey)) {
				UserName = 'Ayon, M. L.';
				ShowLetter = 'firstCircle';
			} else if (import.meta.env.VITE_FC_A3.includes(Passkey) || import.meta.env.VITE_FC_A3_N.includes(Passkey)) {
				UserName = 'Baisa, J. A.';
				ShowLetter = 'firstCircle';
			} else if (import.meta.env.VITE_FC_A4.includes(Passkey) || import.meta.env.VITE_FC_A4_N.includes(Passkey)) {
				UserName = 'Baliuag, V. R.';
				ShowLetter = 'firstCircle';
			} else if (import.meta.env.VITE_FC_A5.includes(Passkey) || import.meta.env.VITE_FC_A5_N.includes(Passkey)) {
				UserName = 'De Leon, T. A.';
				ShowLetter = 'firstCircle';
			} else if (import.meta.env.VITE_FC_A6.includes(Passkey) || import.meta.env.VITE_FC_A6_N.includes(Passkey)) {
				UserName = 'Venturero, J. P.';
				ShowLetter = 'firstCircle';
			} else if (
				Passkey == import.meta.env.VITE_FCSC_A1 ||
				Passkey == import.meta.env.VITE_FCSC_A2 ||
				Passkey == import.meta.env.VITE_FCSC_A3 ||
				Passkey == import.meta.env.VITE_FCSC_A4
			) {
				Attempts--;
				showAttempts = 'Attempts: ' + Attempts;
				pHolder = 'What in the ever living fuck did you just type?';
				Passkey = null;
			} else if (Passkey == null || Passkey == '') {
				Attempts--;
				showAttempts = 'Attempts: ' + Attempts;
				pHolder = "What part of 'type your name' don't you understand?";
				Passkey = null;
			} else {
				Attempts--;
				showAttempts = 'Attempts: ' + Attempts;
				pHolder = 'I said your name, not ' + Passkey + '.';
				Passkey = null;
			}
		} else if (CircleType == circleSelection[1]) {
			//secondCircle
			if (Passkey == ' ') {
				Attempts--;
				showAttempts = 'Attempts: ' + Attempts;
				pHolder = "Adding space ain't gonna work, you understand?";
				Passkey = null;
			} else if (import.meta.env.VITE_SC_A1.includes(Passkey) || import.meta.env.VITE_SC_A1_N.includes(Passkey)) {
				UserName = 'Cabrera, K. C.';
				ShowLetter = 'secondCircle';
			} else if (import.meta.env.VITE_SC_A2.includes(Passkey) || import.meta.env.VITE_SC_A2_N.includes(Passkey)) {
				UserName = 'Cabrera, M. A.';
				ShowLetter = 'secondCircle';
			} else if (import.meta.env.VITE_SC_A3.includes(Passkey) || import.meta.env.VITE_SC_A3_N.includes(Passkey)) {
				UserName = 'Estipona, K. J.';
				ShowLetter = 'secondCircle';
			} else if (import.meta.env.VITE_SC_A4.includes(Passkey) || import.meta.env.VITE_SC_A4_N.includes(Passkey)) {
				UserName = 'Margate, J.';
				ShowLetter = 'secondCircle';
				if (localStorage.getItem('letterKey') == import.meta.env.VITE_TM_10_T)
				{
					addKeys = 'TM-10';
				}
			} else if (import.meta.env.VITE_SC_A5.includes(Passkey)) {
				UserName = 'Marson, M. K.';
				ShowLetter = 'secondCircle';
			} else if (import.meta.env.VITE_SC_A6.includes(Passkey) || import.meta.env.VITE_SC_A6_N.includes(Passkey)) {
				UserName = 'Pagulayan, E.';
				ShowLetter = 'secondCircle';
			} else if (Passkey == null) {
				Attempts--;
				showAttempts = 'Attempts: ' + Attempts;
				pHolder = "Preferably with a name in the textbox.";
				Passkey = null;
			} else if (
				Passkey == import.meta.env.VITE_FCSC_A1 ||
				Passkey == import.meta.env.VITE_FCSC_A2 ||
				Passkey == import.meta.env.VITE_FCSC_A3 ||
				Passkey == import.meta.env.VITE_FCSC_A4
			) {
				Attempts--;
				showAttempts = 'Attempts: ' + Attempts;
				pHolder = 'What in the ever living fuck did you just type?';
				Passkey = null;
			}  else {
				Attempts--;
				showAttempts = 'Attempts: ' + Attempts;
				pHolder = 'I said your name, not ' + Passkey + '.';
				Passkey = null;
				
			}
		}
		if (Attempts == 0) {
			alert('Max attempts reached. You will now be redirected to the homepage.');
			goto(base + '/');
		}
	};
	$: {
		let valueCheck;
		pHolder = 'Use proper capitalization please.';
		if (CircleType == circleSelection[0]) {
			Question = import.meta.env.VITE_FC_Q;
			// Add logic for new modal. Once name of an IC member has been inputted, the letter must immediately show the letter.
			//add code here
		} else if (CircleType == circleSelection[1]) {
			Question = import.meta.env.VITE_SC_Q;
		}
		// let queryParams = $page.url.searchParams.get('accessToken');
		onMount(async () => {
			valueCheck = localStorage.getItem('letterKey');
			//  || queryParams == import.meta.env.VITE_DevPass || queryParams == import.meta.env.VITE_VDPass
			for (let index = 0; index > tokenFinder.length; index++) {
				if (valueCheck == tokenFinder[index]) 
				{

				} 
				else 
				{
					goto(base + '/');
				}
			}
		});
	}
</script>
<title>Hello</title>
{#if UserName}
	<div class="text-center m-5">Welcome, {UserName}</div>
	<div class="cheatline text-center">Letter finished: October 9, 2024</div>
{:else}
	<div class="text-center m-5 text-2xl">
		Welcome, please select your circle and identify yourself.
	</div>
	<!-- <div class="cheatline text-center">‎</div> -->
	<div class="cheatline text-center">Each person may or may not have an additional paragraph to the general letter.</div>
{/if}
{#if !ShowLetter}
	<p class="text-2xl bold text-center m-5">From what circle are you?</p>
	<div class="flex justify-center max-sm:block">
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold tracking-tight ">1st circle / The Alumnis</h5>
				<p class="mb-3 font-normal leading-tight">Since SHS.</p>
				<Button class="bg-bgBlackWhite border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]" on:click={()=>((CircleType = 'TA/1C'), (showModal = true))}>
				Open letter
				</Button>
			</Card>
		</div>
		<div class="overflow-hidden mb-5 flex justify-center mx-5">
			<Card class="bg-current text-[#f5f3f3]">
				<h5 class="mb-2 text-2xl font-bold ">2nd circle / The Starlights</h5>
				<p class="mb-3 font-normal leading-tight">Since 3Y2 and 4Y2.</p>
				<Button class="bg-bgBlackWhite border border-[#dddddd] hover:bg-[#dddddd] hover:text-[#313131]" on:click={()=>((CircleType = 'TS/2C'), (showModal = true))}>
					Open letter
				</Button>
			</Card>
		</div>
	</div>
{/if}

<!-- First circle letter start -->
{#if ShowLetter == 'firstCircle'}
	<article class="m-10 mb-3">To my first circle / The Alumnis</article>
	<article class="m-10">
		Hello guys, salamat sa inyo. Bakit ako nag papasalamat? lately, narealize ko kung ano yung mangyayari if tinuloy ko. 
		Paano? May nakita akong <a class="cursor-pointer underline" href="https://www.tiktok.com/@chickenbangshardasf/photo/7403949446108663072?is_from_webapp=1&sender_device=pc&web_id=7363649119540495888">slideshow sa TikTok,</a> 
		Dahil doon, salamat sa inyo kase buhay pa ako. Tinanggap niyo ako kahit na ako ay nagiging gago pa minsan-minsan. Nakakaproud nga kayo eh, parang dati, ako yung nagtuturo sa inyo.
		Ngayon naman, kayo na ang nagtuturo sa akin. Tapos ang bondings pa natin na minsan biglaan or sa times na ako ay may ginagawang kagaguhan. Kahit minsan lang tayo mag bondinng in person,
		Madalas naman tayo nasa Discord para makipaggaguhan, tulungan sa code, mag dance battle, at kung ano pa. Sorry sa times na irritable ako or nagiging shunga minsan.
	</article>
	<article class="m-10">
		Hindi ko din kase alam
		kung saan talaga papunta tong pinagagawa ko minsan. Pero still, nandyan pa din kayo sa akin. I'm thankful for that. Thankful ako na kayo yung inner circle ko. Kinaibigan niyo ako hindi dahil sa isang bagay, 
		kinaibigan niyo ako kase ako yon at tinanggap niyo ako whole-heartedly, even through ups and downs. Yung tipong bigla kayong pupunta
		dito nang walang reason or yun nga, makikipagkwentuhan sa Discord nang wantusawa hanggang sa mawalan na ng kwento o tsismis, unless magkaroon kayo ng random bullshit thoughts na biglang lalabas
		sa bibig niyo. At least nagbibigay saya kayo sa akin nang hindi niyo alam. Mahal na mahal ko kayo. Thank you sa 6+ years worth ng bondings, memories, kagaguhan, supporta and especially, thank you for saving my life. May God have mercy on our souls.
	</article>
	<article class="m-10">
		Kung tatanungin niyo kung bakit the Alumnis ang tawag ko sa circle natin, eh syempre, grumaduate tayo sa iisang school nung SHS eh. Kaya ganyan ang naming ko minsan sa circle natin.
		Alam ko na isa sa inyo ang nakakita ng kapakshitan sa modal kase tinesting niyo kung racism niyo doon.
	</article>
	<footer class="m-10 mr-18 text-end">
		From your personal photographer, IT HelpDesk, and close friend, <br />
		Hanz Edilberto O. Lizaso III
	</footer>
	<hr />
	<!-- First circle letter end -->
	<!-- Second circle letter start -->
{:else if ShowLetter == 'secondCircle'}
	<article class="m-10 mb-3">To my second circle / The Starlights</article>
	<article class="m-10">
		Hello guys, salamat sa inyo. Sa mga memories, bondings, random photoshoots, kagaguhan, at kung saan pa. Nakakatuwa at kayo pa yung naging 2nd circle ko, Kayo pa yung pumalit sa dati ko na circle na pinilit ko sarili ko doon 
		and to be honest, happy na ako sa current 2nd circle ko. Kinaibigan niyo ako hindi dahil sa isang bagay, kinaibigan niyo ako kase ako yon at tinanggap niyo ako whole-heartedly. Ginawa ko tong letter na ito for a reason.
		Dahil <a class="cursor-pointer underline" href="https://www.tiktok.com/@chickenbangshardasf/photo/7403949446108663072?is_from_webapp=1&sender_device=pc&web_id=7363649119540495888">dito,</a> mas lalo ko pa narealize yung possible
		scenarios kung tinuloy ko. Naoverwhelmed ako sa scenarios. Kung ano magbabago sa buhay niyo at ng pamilya ko. As in grabe lang na. 
	</article>
	<article class="m-10">
		I can't comprehend yung mga scenarios na iyon. Ang sakit sa puso. Thankful ako sa inyo kase niligtas
		niyo ako. Especially sa times na napapansin niyo na hindi ko na kaya. Nagsasabi naman ako sa inyo if kaya ko ikwento sa inyo. I'm sorry sa times na hindi ako nakikinig sa inyo, sa pagiging needy, irritable, and sa pagiging shunga ko. Thankful ako kay God dahil kayo yung naging kaibigan ko, kahit may ups and downs, kahit 2+ years to less than
		a year pa lang ang pagsasama natin, magkaibigan pa din tayo. Yung tipong nagkaroon na ako ng school daughters at school sisters dahil doon. Hindi ako nagrereklamo, ang saya ko nga eh. Dumagdag pa legacy ko sa school and sa inyo.
		Sana soon, makumpleto tayo ulit. Kase mas masaya kung magkasama tayong lahat. At least nagbibigay saya kayo sa akin nang hindi niyo alam. Mahal na mahal ko kayo. Thank you sa 1 year worth ng bondings, memories, kagaguhan, supporta and especially, thank you for saving my life. May God have mercy on our souls.
	</article>
	{#if addKeys == 'TM-10'}
		<article class="m-10">
			Ikaw naman anakis, kalma lang sa life ha? kaya mo yan. Nandito lang naman ako sa side mo eh. Kung ano man problems mo, nandito ang school father mo ha? Icocomfort kita. Sana soon makita na kita ulit.
			Nakakamiss ka. Bwisitin. HSHSAHAHAHHASHA hinde ano, nakakamiss ka na talaga. Sana talaga makita kita soon kase namimiss ko na anakis ko at ang yakap niya. Remember, nandito ang school father mo for you, oki?
			See u soonest anakis, I love you so much. Alam mo yan. Thank you so much for everything, especially for saving my life. God bless you and ingat ka palagi.
		</article>
	{/if}
	<article class="m-10">
		Kung tatanungin niyo kung bakit the Starlights ang tawag ko sa circle natin, well, dahil naman sa lahat kayo ay babae at ako lang ang lalaki dito. At tsaka oo, magaganda kayo and naisip ko na
		ibagay kayo sa Starlight, kase nga, maganda tignan. Kaya ganyan ang naming ko minsan sa circle natin.
	</article>
	<footer class="m-10 mr-18 text-end">
		From your personal photographer, not related brother, school brother and father, supporter, and close friend, <br />
		Hanz Edilberto O. Lizaso III
	</footer>
	<hr />
{/if}
<!-- Second circle letter end -->
{#if ShowLetter}
	<div class="text-center m-5">If you want, please leave a message to the developer.</div>
	<form on:submit|preventDefault={sendEmail}>
		<div class="flex justify-center">
			<input
				type="text"
				placeholder="Name"
				name="from_name"
				class=" border rounded-lg text-black m-4 p-1 inputColor"
				required
			/>
		</div>
		<div class="flex justify-center">
			<textarea
				name="message"
				placeholder="Message"
				class="border rounded-lg inputColor p-1"
				required
			></textarea>
			<button
				type="submit"
				value="Send"
				class="border rounded-lg p-2 mt-auto mb-auto ml-5 buttonChange"
			>
				send
			</button>
		</div>
	</form>
	<button class="m-10 float-end border rounded-lg p-2" on:click={() => goto(base + '/')}>
		<Icon icon="ep:back" style="color: #dddddd" />
	</button>
{/if}
{#if !UserName}
	<Modal bind:showModal>
		<h2 slot="header" class="text-2xl text-center border-b-2 border-bgBlack">Passphrase</h2>
		<p class="text-base text-center">{showAttempts}</p>
		<p class="text-base text-center text-[#991b1b]">{pHolder}</p>
		<p class="text-base text-center">{Question}</p>
		<form on:submit|preventDefault={verifier} class="text-center">
			<input
				type="text"
				class="border-b-2 rounded-sm m-2"
				placeholder="Answer"
				bind:value={Passkey}
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
	.inputColor {
		color: #313131;
	}
	:global(html) {
		background-color: theme(colors.bgBlackWhite);
		color: #dddddd;
	}
	@media screen and (max-width: 600px) {
		.buttonChange {
			margin-right: 12px;
		}
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
