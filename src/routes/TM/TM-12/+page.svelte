<script>
	// @ts-nocheck

	import CMA from '$lib/assets/TM/MA.jpg?url';
	import CMA1 from '$lib/assets/TM/MA1.jpg?url';
	import CMA2 from '$lib/assets/TM/MA2.jpg?url';
	import CMA3 from '$lib/assets/TM/MA3.jpg?url';
	import CMA4 from '$lib/assets/TM/MA4.jpg?url';
	import CMA5 from '$lib/assets/TM/MA5.jpg?url';
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

<title>Hai, Asliiii</title>
<div class="text-center m-5">Welcome, Cabrera, M. A.</div>
<div class="cheatline text-center">Page updated: December 3, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
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
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Birthday letter</h5>
			<p class="mb-3 font-normal leading-tight blur-md">
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

	<!-- //* for graduation | 2027 -->
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CMA5} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Being drafted</h5>
			<p class="mb-3 font-normal leading-tight">Draft is hidden as per my decision.</p>
			<Button
				class="bg-bgPink border border-[#fd5da8] hover:bg-[#fd5da8]"
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
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center">Birthday letter</h2>
			<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: December 3, 2024 | Letter written: December 5/6, 2024
			</p>
			<h3 class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter to be shown by 10:00 PM of December 6.
			</h3>
			<div class="text-[#f5f3f3] blur-lg">
				<article class="m-5">
					Hai Asliiii, HAPPY 22ND BIRTHDAY SAYOOOOO!!! We both know na hindi lang ito ang gift ko
					sayo, may photoshoot ka and syempre, yung prescence ko sa birthday mo or better yet, sa
					life mo. Anyways, I know na babasahin mo to sa birthday mo mismo, whether it be yung
					written version ng letter or eto. Grabe no, more than 1 year na ang pagkakaibigan natin
					pero sobrang close na natin. Tamang bardagulan and whatever na want mo na gawin na kasama
					ako/kami, naging comfy ka ba naman eh. At least happy ka diba? yan ang importante. Keep
					yourself happy lang my Asli ha? Bago ko ilahad ang history natin from first chat to
					present, Ang wish ko for you is for you to be successful in life and be happy, stay
					beautiful and awesome, have your dreams come true, and of course, you become the best
					version of you that you've always wanted.
				</article>
				<article class="m-5">
					Ilalahad ko history ng pagkakaibigan natin mula sa first chat mo. Nung nagchat ako sayo
					nung Mental health week nung A.Y. 2023-2024, yung sinend ko sayo yung pictures mo nung
					event. Tapos sinabi mo pa sa akin na may trabaho ka tas yun pala naglalaro ka lang nung
					cooking game. Akala ko talaga working student ka HAHAHAHA! Tapos after non dare-daretso na
					tayo sa pag chat. Naging close tayo over time, kahit bago ako mag OJT nagbabardagulan na
					tayo eh. Tapos nung nag EK tayo, nag hide and seek pa tayo. Kaso ang na seek ko ay si Kat
					Kat at ikaw naman ay tinaguan ko. Sorry talaga doon beh, akala ko talaga makikita kita
					ulit noon, pero bumabawi naman na ako sayo thru photoshoots eh. Tapos during OJT naman,
					nakakapagrant ako sayo nung mga times na nabbwisit ako sa OJT, Kahit din ikaw nagrarant
					din about sa schoolworks, problems sa life, or kapag may chismis ka about something,
					sasabihin mo sa akin. Minsan nga, nagpapatulong ka sa akin sa schoolworks mo kahit may OJT
					ako eh. Okay lang naman, madali naman yung mga schoolworks mo eh. Ang saya din naman kase
					natutulungan kita and nakakapagchismisan tayo sa isa't isa, I can say na nag bigay saya ka
					sa akin during internship ko and nakakaproud ka for that Asli. Then next, is yung mga
					photoshoots mo. Ang dami natin naset, eight or nine na ata eh, kasama na yung photoshoot
					natin sa Parqal. It's obvious naman na una kitang na kilala at naging close bago ko
					makilala si Kat Kat, kaya mas marami yung sayo.
				</article>
				<article class="m-5">
					Elaborate ko pa yung sa rants mo, unahin ko yung sa times na nag ooverthink ka sa mga
					grades mo. Sabi ko nga sayo na kaya mo yan, hindi mo need mag alala kase matataas naman
					ang scores mo sa activities. Nagagawa mo nga yung mga school stuffs mo ng maayos eh. Kaya
					don't worry about sa grades mo, You're doing your best naman and I'm always proud of you.
					Always. Kahit hindi ka na pasok sa Cum Laude, I'm still proud of you Ash. Huwag mo
					panghinaan loob mo dahil lang sa may mababa ka na grade. Mababawi yan. Tiwala lang. Yung
					next naman is about sa life, yung mga problems mo and what not. I will be here to listen
					and help you. Aayusin natin yan beh, matagal man yan or hindi. I don't know kung kailan mo
					want pero I'll be here waiting for you. Daig ko pa magiging partner mo eh no? Keep doing
					your best ha? May mga pagsubok ka na dadaanan sa mga susunod na semesters, OJT, and after
					graduation. Makakaraos ka doon if you believe in yourself. Nakakaraos ka nga sa mga
					schoolworks and other problems mo with ease eh. Well not immediately pero at least
					nakakaraos. Oh diba? Kung kinaya mo yon, Kakayanin mo yung ibang pagsubok. Kaya mo yan
					Asli, I know you can, Ikaw yan eh. I'm so grateful to God kase nakilala kita Ash, nandiyan
					ka palagi for me, nakakapagrant tayo sa isa't isa para mapakalma natin ang sarili natin,
					nakakapagshare tayo ng kanta or memes, or anything na want natin, and syempre, magkavibes
					pa tayo.
				</article>
				<article class="m-5">
					I hoped that you enjoyed your birthday Ash. Susupportahan kita no matter what, hindi ako
					mapapagod na tulungan ka, turuan ka, supportahan ka, at samahan ka sa mga endeavors mo
					Ash, I mean that. I love you so much Ashleyyyyy. I wish you all the best mi hermana.
					Alagaan and ingatan mo sarili mo Asli. Again, I will always be here for you. Remember
					that beh. God bless u and ingat ka palagi! Happy birthday ulit Asliiii!!! To more
					kagaguhan and beautiful memories with u!!!
				</article>
				<footer class="m-5 text-end">
					From your not related brother, personal photographer, English teacher, supporter, and close friend, <br
					/>
					Hanz
				</footer>
			</div>
		</Modal>
	{:else if letterContent === 'Graduation'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center blur-md">
				Graduation letter
			</h2>
			<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Letter finished: 2026/2027 | Letter written: 2027
			</h3>
			<div class="text-[#f5f3f3]">
				<article class="m-5">Hai Asliiii, bat ka nandito eh wala pang laman to</article>
				<article class="m-5">
					Matagal pa to bago ako magdraft dito so galingan mo sa school and sa life ikaw oki?
				</article>
				<div class="hidden">
					<article class="m-5">
						CONGRATULATIONS MY ASLIIII!!!! //multiple additionals for letter | helping, supporting,
						and teaching her<br />
					</article>
					<article class="m-5"></article>
					<article class="m-5">
						Marykate Ashley B. Cabrera | Batch 2027 <br />
						Bachelor of Science in Tourism Management <br />
						School Spirit Awardee <br />
						Cum Laude
					</article>
					<footer class="m-5 text-end">
						From your not related brother, personal photographer, supporter, guide, teacher, and
						close friend, <br />
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
