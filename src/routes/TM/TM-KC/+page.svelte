<script>
	// @ts-nocheck

	import CKC from '$lib/assets/TM/KC.jpg?url';
	import CKC1 from '$lib/assets/TM/KC1.jpg?url';
	import CKC2 from '$lib/assets/TM/KC2.jpg?url';
	import CKC3 from '$lib/assets/TM/KC3.jpg?url'; //unused
	import CKC4 from '$lib/assets/TM/KC4.jpg?url';
	import CKC5 from '$lib/assets/TM/KC5.jpg?url'; //unused
	import CKC6 from '$lib/assets/TM/KC6.jpg?url';
	import CKC7 from '$lib/assets/TM/KC7.jpg?url'; //unused
	import CKC8 from '$lib/assets/TM/KC8.jpg?url';
	import CKC9 from '$lib/assets/TM/KC9.jpg?url';
	import CKC10 from '$lib/assets/TM/KC10.webp?url';
	import CKC11 from '$lib/assets/TM/DSC_49sadsaddsa21.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle, Spinner } from 'flowbite-svelte';
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
			if (hasItem && valueCheck == import.meta.env.VITE_TM_KC_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>

<!-- //! change image cards to the latest pictures, if necessary. -->

<title>Henlo, Kat Kattttt</title>
<div class="text-center m-5">Welcome, Cabrera, K. C.</div>
<div class="cheatline text-center">Page updated: December 8, 2024</div>
<header class="mb-5 flex justify-center">
	<img src={CKC9} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" />
</header>
<hr />
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">Please select the letter that you want to read.</p>
</header>

<div class="flex justify-center max-sm:block">
	<div class="overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC} reverse={false} class="bg-current text-[#f5f3f3]">
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
		<Card img={CKC4} reverse={false} class="bg-current text-[#f5f3f3]">
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
		<Card img={CKC8} reverse={false} class="bg-current text-[#f5f3f3]">
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

	<!-- //* for graduation letter -->
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC11} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Being drafted</h5>
			<p class="mb-3 font-normal leading-tight">Draft is hidden as per your request and mine.</p>
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
					Hai Kat Kattt, mag thank u lang ako sa mga memories na nagawa natin together and sa kung
					saan pa. Alam mo, mamimiss kita ng sobra sobra. Kase araw araw ako pumapasok tas araw araw
					din kita nakikita. Tapos kung want mo magphotoshoot, ginagawa naman natin. Hindi lang
					dahil sa crush kita and what not, dahil sa malapit kita na kaibigan and syempre, memories
					mo na din yon sa school pag nakagraduate ka na. Thank you dahil sa naging inspiration and
					motivation kita! Alam mo naman na kung bakit kita nagustuhan eh. Pero sabihin ko ulit,
					Maganda ka, mag ka-vibes tayo, same tayo ng music taste, hindi ka naninigarilyo, and
					syempre mabait ka.
				</article>
				<article class="m-5">
					Sana talaga maging Cum Laude graduate ka. I'm rooting for you beh. Palagi mo tandaan na
					nandito ako para sayo, kahit anong mangyari. Nakakatuwa din na naging close friend kita.
					Ang saya kase ng usapan natin palagi eh, tamang VMs, purong kapakshitan (AMEX PLATINUM,
					GALVANIZED SQUARE STEEL), tas sa mga nanggugulo sayo. Ang saya mo talaga kausap Kat Kat.
					To be honest beh, ikaw yung isa sa mga tao na ginawang bearable ang internship ko dahil sa
					kayo yung nilalapitan ko about doon. Rant dito about sa pinapagawa, rant doon sa kasabay
					ko, you get the point naman. Thank you, kase available ka kausapin if mag rant ako or
					chismis or what not. Sana ganon ka din in the future, pero if sasabihin mo na busy ka,
					hindi naman kita pipilitin. Basta mailahad ko lang yung want ko sabihin, masaya na ako. As
					long na nabasa mo. Tsaka next time, 'wag na kayong mag-away na magkapatid nang
					basta-basta. Nahirapan ako na ikalma kayong pareho noon eh. Pero if ever na mangyari ulit
					yon, kahit ako ulit ang gawin niyong mediator. Wala ako problem doon. Basta na ako lang
					ang mediator niyo.
				</article>
				<article class="m-5">
					Sorry sa mga times na nagiging needy ako sa replies mo kahit alam ko na busy ka ng sobra
					and sa times na hindi kita natutulungan sa schoolworks or sa pagbigay ng advice during
					rants mo kase nablangko utak ko. Tsaka pala, if need mo ng kausap about sa life or
					schoolworks or kung ano man yan, I'm here for you. Alam mo yan beh. Kahit na kausap ko
					kapatid mo about sa rants niya, kinakausap pa din kita about sa rants mo. Tsaka yung sa
					photoshoots natin, ang saya din non. Why? kase ikaw yung una ko naging personal
					model/subject sa mga photoshoots. Tsaka ang dami na din natin na photoshoots ah (3 or 5 na
					ata). Hindi mo pa naman nasasakop ng pictures mo yung SD card kaya safe ka pa. If want mo
					mag photoshoot, sabihan mo lang ako, alam ko naman na want mo din eh. Sasabihan naman kita
					kung free ako. Tsaka mag photoshoot/gala tayo minsan beh, pwedeng tayo lang dalawa or
					kasama si Asli, si Fem, or kung sino pa na want mo isama. Tsaka eto, 'wag mo isipin
					problems mo sa life as much as possible. Mag focus ka sa studies mo pa. Tignan mo ilang
					semesters na lang, tapos ka na. May latin honors pa. Sana talaga Kat na makatapos ka with
					latin honors. Like I said kanina, I'm rooting for you and I'll support you every step of
					the way.
				</article>
				<article class="m-5">
					I'm so thankful na nakilala kita Kat Kat, actually thankful ako sa inyong magkapatid. Ang
					ganda ng pinagsamahan natin kahit nung January lang tayo nag start na mag usap. So yun nga
					beh, thank you again sa mga memories, bondings, and for being my inspiration and
					motivation for this last semester. Mahal na mahal kita Kat. Pareho ko kayong mahal
					magkapatid. God bless u and ingat ka palagi. To more memories with u!!!
				</article>
				<footer class="m-5 text-end">
					From your personal photographer and close friend, <br />
					Hanz
				</footer>
				<article class="m-5">
					P.S. Hindi ko makakalimutan yung time na nagmadali ako na umalis para lang kunin yung
					phone mo sa school. Umiiyak ka pa non tas pinapakalma pa kita habang nagmamadali aq
					magbike. Mystery adventure ba naman eh. Pero hey, hindi naman ako nagalit nung time na yon
					and buti sinabihan mo agad ako noon. Alam ko naman na nag change ka na ng phone, pero
					still, good memories yung nakuha ko noon.
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
				<img src={CKC10} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" />
			</div>
			<div class="text-[#f5f3f3]">
				<article class="m-5">
					Hai Kat Kattttt, HAPPY 22ND BIRTHDAY SAYOOOOO!!! We both know na hindi lang ito ang gift
					ko sayo, may photoshoot ka and syempre, yung prescence ko sa birthday mo or better yet, sa
					life mo. Anyways, I know na babasahin mo to sa birthday mo mismo, whether it be yung
					written version ng letter or eto. By the way, you can say na yung binigay ko sayo na
					bracelet is regalo ko na sayo for your birthday, Kahit na sobrang early ko binigay sayo
					yon (around May ata yon or June eh). Huwag mo iwala yon Kat Kat, friendship bracelet natin
					'yon (Suot man natin yan or hindi). I'll be grateful kung makita ko na suot mo yon minsan.
					Grabe no, almost 1 year na ang pagkakaibigan natin pero close na close na tayo. Tamang
					bardagulan lang and whatever na want mo na gawin na kasama ako/kami, naging comfy ka ba
					naman eh. At least happy ka diba? ayan ang importante. Keep yourself happy lang my Kat Kat
					ha? Bago ko ilahad ang history natin from first chat to present, Ang wish ko for you is
					for you to be successful in life, stay beautiful, stay awesome, and of course, have your
					dreams come true, lalo na yung pagiging Cum Laude mo.
				</article>
				<article class="m-5">
					Now, ilalahad ko history ng pagkakaibigan natin mula sa first chat mo. Nung nagchat ka sa
					akin ng "Papitik nga" nung intrams kase kilala mo ako bilang student photographer nung
					school tapos akala ko pa nga nandun ka sa school non so hinanap kita pero syempre, nag
					send ako ng pic ko noon na ipipitik kita (literal) tapos dare-daretso na tayo sa pag chat.
					Naging close tayo during OJT ko, yung kapag may free time tayong dalawa, mag uusap tayo
					hanggang sa maging busy tayo. Buti nga nakakapagrant ako sayo nung mga times na nabbwisit
					ako sa OJT noon, tas ikaw naman nagrarant din about sa schoolworks or anything about sa
					school or life. Minsan tinutulungan kita sa schoolworks mo kapag nahihirapan ka, like yung
					sa entrep and Euthenics mo (yung nilagyan ko ng "taga gawa ng fakeshit" yung résumé mo).
					Ang saya nga kase nasasabi ko sa sarili ko na, "Natutulungan ko yung tinutulungan ako." or
					"Natutulungan ko yung kapatid ko". Before kase, "Natutulungan ko yung crush ko". Tsaka
					nakakapagchismisan tayo sa isa't isa. It's obvious na nag bigay saya ka sa akin during
					internship ko and nakakaproud ka for that Kat Kat. Then next, is yung mga photoshoots mo.
					Ang dami natin naset, seven or eight na ata eh, kasama na yung photoshoot natin sa Parqal.
				</article>
				<article class="m-5">
					Elaborate ko pa yung sa rants mo, especially yung sa times na nag ooverthink ka sa mga
					grades mo. Sabi ko nga sayo na kaya mo yan, hindi mo need mag alala kase matataas naman
					ang scores mo sa activities and TPs. Nagagawa mo nga yung mga school stuffs mo ng maayos
					eh, pasok ka niyan sa Cum Laude Kat Kat, I promise you that. Kaya don't worry about sa
					grades mo, You're doing your best naman and I'm always proud of you. Always. Keep doing
					your best ha? Not just in school, but sa life din. May mga pagsubok ka na dadaanan sa OJT
					and after graduation, and makakaraos ka doon if you believe in yourself. Nakakaraos ka nga
					sa mga schoolworks and other problems mo with ease eh. May technique ka pa nga minsan para
					doon, "Walang pakialam sa paligid". At least may ways ka. Oh diba? Kung kinaya mo yon,
					Kakayanin mo yung ibang pagsubok. Kaya mo yan Kat Kat, I know you can, Ikaw yan eh. If may
					times na hindi mo kaya, I will be here to listen to you and samahan ka. Kagaya nga ng
					sinasabi mo sa akin during deep talks natin, Hindi rin ako magiging available palagi, pero
					I'll still listen to you kahit na minsan ay late ako mag reply. Basta ichat mo lang yan,
					babasahin ko naman yan oki? I'm so grateful to God kase nakilala kita Kat Kat, nandiyan ka
					palagi for me, nakakapagrant tayo sa isa't isa para mapakalma natin ang sarili natin,
					nakakapagshare tayo ng kanta or memes, or anything na want natin, and syempre, magkavibes
					pa tayo. Sorry sa mga times na naging needy ako sayo and sa times na nainis ka sa akin. I
					hope na mapatawad mo ako.
				</article>
				<article class="m-5">
					I hoped that you enjoyed your birthday Kat Kat. Susuportahan kita no matter what, hindi
					ako mapapagod na tulungan ka, turuan ka, supportahan ka, at samahan ka sa mga endeavors mo
					or sa kung ano man Kat Kat, I mean that. I love you so much Katrinaaaaa. I wish you all
					the best mi hermana. Alagaan and ingatan mo sarili mo Kat Kat. Again, I will always be
					here for you. Remember that beh. God bless u and ingat ka palagi! Happy birthday ulit Kat
					Kattttt!!! To more kagaguhan and beautiful memories with u!!!
				</article>
				<footer class="m-5 text-end">
					From your not related brother, US Boi, personal photographer, English teacher, supporter,
					and close friend, <br />
					Hanz
				</footer>
				<article class="m-5">
					P.S. I'm really grateful for you being in my life Kat Kat. I know na sinabi ko na yon sa
					letter pero listen, sana magtagal ang friendship natin kase tinuturing na talaga kitang
					kapatid. Nafefeel ko yung love na binibigay mo sa akin, and it feels so nice, that
					sisterly love. You know naman na only child lang ako pero grabe, nafeel ko na may kapatid
					ako dahil sayo. I'm so thankful for you. I'll protect and support you like a brother. I'll
					cherish our friendship forever, mi hermana. I love you so much!
				</article>
			</div>
		</Modal>
	{:else if letterContent === 'Graduation'}
		<Modal bind:showModal>
			<h2 slot="letterType" class="text-white text-xl cheatline text-center blur-md">
				Graduation letter
			</h2>
			<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
				Draft Started: February 27, 2025 | Letter finished: 2025 | Letter written: 2025
			</h3>
			<div class="text-[#f5f3f3]">
				<article class="m-5">
					CONGRATULATIONS MY KAT KATTTT!!!! //multiple additionals for letter | helping,
					supporting, and teaching her<br />
				</article>
				<article class="m-5"></article>
				<article class="m-5">
					Katrina Clarisse B. Cabrera | Batch 2025 <br />
					Bachelor of Science in Tourism Management <br />
					Cum Laude
				</article>
				<footer class="m-5 text-end">
					From your not related brother, personal photographer, supporter, guide, teacher, and
					close friend, <br />
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
			value="Katrina/Kat Kat"
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
