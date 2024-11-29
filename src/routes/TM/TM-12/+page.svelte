<script>
	// @ts-nocheck

	import CMA from '$lib/assets/TM/MA.jpg?url';
	import CMA1 from '$lib/assets/TM/MA1.jpg?url';
	import CMA2 from '$lib/assets/TM/MA2.jpg?url';
	import CMA3 from '$lib/assets/TM/MA3.jpg?url';
	import CMA4 from '$lib/assets/TM/MA4.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let showModal = false;
	let letterContent = '';
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
			if (hasItem && valueCheck == import.meta.env.VITE_TM_12_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>

<title>TM/TM-12</title>
<div class="text-center m-5">Welcome, Cabrera, M. A.</div>
<div class="cheatline text-center">Page updated: November 26, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<!-- //! 3 pictures will be set, pictures can be changed or retained -->
	<img src={CMA4} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" />
</header>
<hr />
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">Please select the letter that you want to read.</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CMA} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Gratitude letter</h5>
			<p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
			<Button
				class="bg-bgPink border border-[#fd5da8] hover:bg-[#fd5da8]"
				on:click={() => letterShow('Gratitude')}
			>
				Open letter
			</Button>
		</Card>
	</div>

	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CMA1} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">To my 2nd circle</h5>
			<p class="mb-3 font-normal leading-tight">Access to cartas secreta.</p>
			<Button
				class="bg-bgPink border border-[#fd5da8] hover:bg-[#fd5da8]"
				on:click={() => letterShow('Reminder')}
			>
				Open letter
			</Button>
		</Card>
	</div>

	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CMA2} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Being drafted</h5>
			<p class="mb-3 font-normal leading-tight">Draft is hidden as per my decision.</p>
			<h5 class="mb-2 text-2xl font-bold tracking-tight hidden">Birthday letter</h5>
			<p class="mb-3 font-normal leading-tight hidden">
				Happy 22nd birthday mi hermana, bff, and model!!!
			</p>
			<Button
				class="bg-bgPink border border-[#fd5da8] hover:bg-[#fd5da8]"
				on:click={() => letterShow('Birthday')}
			>
				Open letter
			</Button>
		</Card>
	</div>
	{#if letterContent === 'Gratitude'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
			<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: June 11, 2024 | Letter written: June 11, 2024
			</p>
			<div class="text-[#f5f3f3]">
				<!-- //* you may add carousel or images in between -->
				<article class="m-5">
					Hai Asliii, Thank u sa lahat ng memories and sa kung saan pa! Alam mo, nahihirapan ako
					gumawa ng letter para sayo, kase ang dami neto eh. Grabe yung first natin na pagkikilala,
					shy type ka ba naman eh HSAHAHAHAH tapos nagpapic ka before and during mental health week
					tas after 7+ months, close friend na kita. Pareho ko pa kayong close na magkapatid ah. Ang
					saya nga eh, don't get me wrong ha. Yung mga random dances mo sa kung saan man, keep mo
					yon ha? Nakikita ko naman na happy ka kapag ginagawa mo yon eh. Hayaan mo kung ano sabihin
					nila basta you do your own thing.
				</article>
				<article class="m-5">
					Alam mo minsan, nag aalala aq sayo. Saan? Sa mga decisions mo sa life and what not. Alam
					mo naman na yon. Ayoko lang kase na magaya ka sa ex-friend ko na tatanga tanga eh. Tapos
					sa lovelife pa nga na sinasabi namin na 'wag mo na lapitan, nilalapitan mo pa din.
					Haynakupo Asli. Pasalamat ka na mahal ka namin. Anyways, balik na tayo sa topic. Ang
					mamimiss ko sayo is yung ugali mo. Most of the time masaya ka naman pero minsan, nagrarant
					ka about sa kung saan diba? Ang malupit kase sayo is natatago mo thru the smiles eh. If
					ever na need mo ng kausap, nandito lang ako beh. Alam mo yan. Kahit kausap ko si Kat Kat
					about sa rants/chismis niya, nagmamake ako ng time sayo about sa rants/chismis mo. Tsaka
					next time, 'wag na kayong mag-away na magkapatid nang basta-basta. Nahirapan ako na ikalma
					kayong pareho noon eh. Pero if ever na mangyari ulit yon, kahit ako ulit ang gawin niyong
					mediator. Wala ako problem doon. Basta na ako lang ang mediator niyo. Huwag ka na mag
					bring up ng iba, Oki?
				</article>
				<article class="m-5">
					About naman sa photoshoots mo, kaya pa naman ng SD card ko ang pagmumukha at kagandahan mo
					kaya no problem don. At kagaya ng sinabi ko kay Kat Kat sa letter niya, If want mo mag
					photoshoot, sabihan mo lang ako, alam ko naman na want mo din eh. Sasabihan naman kita
					kung free ako. Tsaka mag photoshoot/gala tayo minsan beh. Kayo na bahalang magkapatid kung
					sino kasama. Change topic tayo saglit. Pareho kayo ng kapatid mo na running for latin
					honors, diba? Word of advice lang, Magfocus ka na sa pag-aaral. Kase need na need mo yan.
					Hindi ko sinasabi na need mo yon kase mababa grades mo, no, sinasabi ko yon kase minsan,
					nawawala ka sa focus. Alam ko na masayang magkaroon ng crush, pero minsan nafafall ka agad
					eh. Kaya magfocus ka sa sarili mo, sa pag-aaral mo, and sa magiging future mo. Oki? Good.
					Basta yun nga, mag photoshoot tayo minsan ha? Hindi ko sinasabi na nagsasawa na ako kay
					Kat Kat ha? Sinasabi ko lang na ikaw naman ang maging subject/model ko at para naman may
					pics ka sa cam kahit paano. Oo, alam ko may pics ka pero mas lamang na si Kat Kat sa mga
					pics.
				</article>
				<article class="m-5">
					I'm so thankful na nakilala kita Asli, pero mas thankful ako na nakilala ko kayong
					magkapatid. Ang saya ng bonding, kulitan, tuwaan, iyakan, and kung ano pa for the last 7+
					months. Before ko tapusin itong letter, I just wanna say na thank you dahil tinulungan mo
					si Ma'am Alelie nung nahimatay/collapse ako non. Narealize ko na ganon na pala tayo
					kaclose, to the point na kahit pagod ka na, tumakbo at pumunta ka ng clinic para sa first
					aid kit at para sabihan sila Ma'am Anna. Ang laki ng utang na loob ko sayo Ashley. Thank
					you so much. So yun nga, thank you sa mga memories, bondings, and kulitan sa loob ng
					school. Mahal na mahal kita Asli. Pareho ko kayong mahal magkapatid. God bless u and ingat
					ka palagi. To more memories with u!!!
				</article>
				<footer class="m-5 text-end">
					From your personal photographer and close friend, <br />
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
	{:else if letterContent === 'Birthday'}
		<!-- //! birthday letter drafting will start by 2nd week of Oct. or Nov. Will be confidential once drafting starts. -->
		<!-- //! Letter to be written ~ 2 weeks before Dec. 9. Dates may change w/o notice -->
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center blur-sm">
				Birthday letter
			</h2>
			<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: December X, 2024 | Letter written: December X, 2024
			</p>
			<div class="text-[#f5f3f3]">
				<article class="m-5 text-center">
				Wala pa chill lang, dinadraft ko siya as of writing (November 26, 2024 | 6:33 AM) <br/>
				Napakaganda mo talaga doon sa pic na naka black ka na sando (oo maganda ka talaga, alam ko. Sadyang nagandahan ako sa pic mo na yon, and I love it!)
				</article>
				<article class="m-5"></article>
				<article class="m-5"></article>
				<div class="hidden">
					<article class="m-5">
						<!-- //* you may add something more here. -->
						Hai Asliiii, Happy 22nd birthday sayooooo!!! We both know na hindi lang ito ang gift ko
						sayo, may photoshoot ka and syempre, yung prescence ko sa birthday mo or better yet, sa
						life mo. Anyways, I know na babasahin mo to sa birthday mo mismo, whether it be yung
						written version ng letter or eto. Grabe no, 1 year na ang pagkakaibigan natin pero sobrang
						close na natin. Tamang bardagulan and whatever na want mo na gawin na kasama ako/kami,
						naging comfy ka ba naman eh. At least happy ka diba? yan ang importante. Keep yourself
						happy lang my Asli ha?
					</article>
					<article class="m-5">
						<!-- //! reorganize -->
						Ilalahad ko history ng pagkakaibigan natin mula sa first chat mo. Nung nagchat ako sayo
						nung Mental health week nung A.Y. 2023-2024, yung sinend ko sayo yung pictures mo nung
						event. Tapos sinabi mo pa sa akin na may trabaho ka tas yun pala naglalaro ka lang nung
						cooking game. Akala ko talaga working student ka HAHAHAHA! Tapos after non  
						//continue to convo history, search parameter "drive"
						
						
						
						ka sa akin
						ng "Papitik nga" nung intrams kase kilala mo ako bilang student photographer nung school
						tapos akala ko pa nga nandun ka sa school non so hinanap kita pero syempre, nag send ako 
						ng pic ko noon na ipipitik kita (literal) tapos dare-daretso na tayo sa pag chat. Naging 
						close tayo during OJT ko, yung kapag may free time tayong dalawa, mag uusap tayo hanggang 
						sa maging busy tayo. Buti nga nakakapagrant ako sayo nung mga times na nabbwisit ako sa 
						OJT noon, tas ikaw naman nagrarant din about sa schoolworks or anything about sa school.
						Minsan tinutulungan kita sa schoolworks mo kapag nahihirapan ka, like yung sa entrep and
						Euthenics mo (yung nilagyan ko ng "taga gawa ng fakeshit" yung résumé mo). Ang saya nga 
						kase nasasabi ko sa sarili ko na, "Natutulungan ko yung tinutulungan ako." [before na, 
						"Natutulungan ko yung crush ko", ngayon naman ang sinasabi ko is, "Natutulungan ko yung 
						kapatid ko".] Then next, is yung mga photoshoots mo. Ang dami natin naset, seven or eight 
						na ata eh, kasama na yung photoshoot natin sa Parqal.
					</article>
					<article class="m-5">//Third body, personal matters, her rants, and/or struggle for herself</article>
					<article class="m-5">
						I hoped that you enjoyed your birthday Ash. We're here for you, especially me.
						Susupportahan ka namin no matter what, hindi ako mapapagod na tulungan ka, turuan ka,
						supportahan ka Ash, I mean that. I love you so much Ashleyyyyy. I wish you all the
						best mi hermana. Alagaan and ingatan mo sarili mo Asli. Again, I will always be here 
						for you. Remember that beh. Happy birthday ulit Asliiii!!!
					</article>
					<footer class="m-5 text-end">
						From your not related brother, personal photographer, English teacher, and close friend, <br />
						Hanz
					</footer>
				</div>
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
			value="Ashley/Asli"
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
		background-color: #fd5da8;
		color: #eeeeee;
	}
	:global(html) {
		background-color: theme(colors.bgPink);
		color: #dddddd;
	}
	@media screen and (max-width: 700px) {
		img {
			width: 67%;
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
