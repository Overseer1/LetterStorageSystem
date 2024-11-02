<script>
// @ts-nocheck

	import CKC from '$lib/assets/TM/KC.jpg?url';
	import CKC1 from '$lib/assets/TM/KC1.jpg?url';
	import CKC2 from '$lib/assets/TM/KC2.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let showModal = false;
	let letterContent = '';
  	let vCard = false;
	let targetScroll;
	function letterShow(contentSelect){
		letterContent = contentSelect;
		showModal = true;
	}
	function scrollToSection() {
    	targetScroll.scrollIntoView({ behavior: "smooth" });
    }
    const sendEmail = (/** @type {{ target: string | HTMLFormElement; }} */ e) => {
    emailjs
        .sendForm(import.meta.env.VITE_EmailJS_ServiceID, import.meta.env.VITE_EmailJS_TemplateIDFF, e.target, {
        publicKey: import.meta.env.VITE_EmailJS_PublicKey,
        })
        .then(
        () => {
            console.log('SUCCESS!');
			alert("Message sent");
        },
        (error) => {
            console.log('FAILED...', error.text);
        },
        );
    };
	$: {
		let hasItem;
		let valueCheck;
		onMount(async () => {
			hasItem = localStorage.getItem('letterKey') !== null;
			valueCheck = localStorage.getItem('letterKey');
			// Conditional logic based on hasItem
			if (hasItem && valueCheck == import.meta.env.VITE_TM_KC_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>TM/TM-KC</title>
<div class="text-center m-5">Welcome, Cabrera, K. C.</div>
<div class="cheatline text-center">Page updated: November 2, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={CKC1} alt="N/A" class="object-cover mt-5 h-[250px] w-[450px] rounded-lg" />
</header>
<hr/>
<p class="m-5 mb-5 text-center text-xl">As per your request and mine, unfinished letters and sections are obscured. Once finished, it will be unblurred.<br/>
<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
As of writing/developing (November 2, 2024 | 8:56 AM), your letters are being transferred to the new UI. Please click <span class="underline cursor-pointer" on:click={scrollToSection}>this</span> to go to the recent letter.</p>
<header class="overflow-hidden flex justify-center cheatline my-5 blur-md">
	<p class="text-lg">
		Please select the letter that you want to read.
	</p>
</header>
<div class="flex justify-center max-sm:block blur-lg">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC} reverse={vCard} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Gratitude letter</h5>
		  <p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
		  <Button class="bg-bgPurp hover:bg-[#6d28d9]" disabled on:click={()=>(letterShow('Gratitude'))}>
			Read more
		  </Button>
		</Card>
		<!-- <Toggle bind:checked={vCard} class="italic dark:text-gray-500">Reverse</Toggle> -->
	</div>

	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC2} reverse={vCard} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight">Birthday letter</h5>
		  <p class="mb-3 font-normal leading-tight">Happy 22nd birthday mi hermana, bff, and model!!!</p>
		  <Button class="bg-bgPurp hover:bg-[#6d28d9]" disabled on:click={()=>(letterShow('Birthday'))}>
			Read more
		  </Button>
		</Card>
		<!-- <Toggle bind:checked={vCard} class="italic dark:text-gray-500">Reverse</Toggle> -->
	</div>
	
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC1} reverse={vCard} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Graduation letter</h5>
		  <p class="mb-3 font-normal leading-tight">CONGRATULATIONS MI HERMANAAAAAA!!!</p>
		  <Button class="bg-bgPurp hover:bg-[#6d28d9]" disabled on:click={()=>(letterShow('Graduation'))}>
			Read more
		  </Button>
		</Card>
		<!-- <Toggle bind:checked={vCard} class="italic dark:text-gray-500">Reverse</Toggle> -->
	</div>
	{#if letterContent === 'Gratitude'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: June 10, 2024 | Letter written: June 11, 2024 | Letter updated: July 16, 2024</p>
		<div class="text-[#f5f3f3]">
			<!-- //* you may add carousel or images in between -->
			<article class="m-10 mb-3">
				Hai Kat Kattt, mag thank u lang ako sa mga memories na nagawa natin together and sa kung saan pa.
				Alam mo, mamimiss kita ng sobra sobra. Kase araw araw ako pumapasok tas araw araw din kita
				nakikita. Tapos kung want mo magphotoshoot, ginagawa naman natin. Hindi lang dahil sa crush kita
				and what not, dahil sa malapit kita na kaibigan and syempre, memories mo na din yon sa school pag
				nakagraduate ka na. Thank you dahil sa naging inspiration and motivation kita! Alam mo naman na kung bakit kita nagustuhan eh.
				Pero sabihin ko ulit, Maganda ka, mag ka-vibes tayo, same tayo ng music taste, hindi ka naninigarilyo, and syempre mabait ka.
			</article>
			<article class="m-10">
				Sana talaga maging Cum Laude graduate ka. I'm rooting for you beh. Palagi mo tandaan na nandito
				ako para sayo, kahit anong mangyari. Nakakatuwa din na naging close friend kita. Ang saya kase ng
				usapan natin palagi eh, tamang VMs, purong kapakshitan (AMEX PLATINUM, GALVANIZED SQUARE STEEL), tas sa mga
				nanggugulo sayo. Ang saya mo talaga kausap Kat Kat. To be honest beh, ikaw yung isa sa mga tao na
				ginawang bearable ang internship ko dahil sa kayo yung nilalapitan ko about doon. Rant dito about
				sa pinapagawa, rant doon sa kasabay ko, you get the point naman. Thank you, kase available ka
				kausapin if mag rant ako or chismis or what not. Sana ganon ka din in the future, pero if
				sasabihin mo na busy ka, hindi naman kita pipilitin. Basta mailahad ko lang yung want ko sabihin,
				masaya na ako. As long na nabasa mo. Tsaka next time, 'wag na kayong mag-away na magkapatid nang basta-basta.
				Nahirapan ako na ikalma kayong pareho noon eh. Pero if ever na mangyari ulit yon, kahit ako ulit ang gawin niyong mediator.
				Wala ako problem doon. Basta na ako lang ang mediator niyo.
			</article>
			<article class="m-10">
				Sorry sa mga times na nagiging needy ako sa replies mo kahit alam ko na busy ka ng sobra and sa times na
				hindi kita natutulungan sa schoolworks or sa pagbigay ng advice during rants mo kase nablangko utak ko. 
				Tsaka pala, if need mo ng kausap about sa life or schoolworks
				or kung ano man yan, I'm here for you. Alam mo yan beh. Kahit na kausap ko kapatid mo about sa rants niya, kinakausap pa din kita about sa rants mo.
				Tsaka yung sa photoshoots natin, ang saya din non. Why? kase ikaw yung una ko naging personal
				model/subject sa mga photoshoots. Tsaka ang dami na din natin na photoshoots ah (3 or 5 na ata).
				Hindi mo pa naman nasasakop ng pictures mo yung SD card kaya safe ka pa. If want mo mag photoshoot, sabihan mo lang ako, alam ko naman na want mo din eh.
				Sasabihan naman kita kung free ako. Tsaka mag photoshoot/gala tayo minsan beh, pwedeng tayo lang dalawa or kasama si Asli, si Fem, or kung sino pa na want mo isama.
				Tsaka eto, 'wag mo isipin problems mo sa life as much as possible. Mag focus ka sa studies mo pa. Tignan mo ilang semesters
				na lang, tapos ka na. May latin honors pa. Sana talaga Kat na makatapos ka with latin honors. Like
				I said kanina, I'm rooting for you and I'll support you every step of the way.
			</article>
			<article class="m-10">
				I'm so thankful na nakilala kita Kat Kat, actually thankful ako sa inyong magkapatid. Ang ganda ng pinagsamahan natin kahit nung January lang
				tayo nag start na mag usap. So yun nga beh, thank you again sa mga memories, bondings, and for
				being my inspiration and motivation for this last semester. Mahal na mahal kita Kat. Pareho ko kayong mahal magkapatid. God bless u
				and ingat ka palagi. To more memories with u!!!
			</article>
			<footer class="m-10 mr-18 text-end">
				From your personal photographer and close friend, <br />
				Hanz
			</footer>
			<article class="m-10">
				P.S. Hindi ko makakalimutan yung time na nagmadali ako na umalis para lang kunin yung phone mo sa school. Umiiyak ka pa non tas pinapakalma pa kita habang nagmamadali aq magbike.
				Mystery adventure ba naman eh. Pero hey, hindi naman ako nagalit nung time na yon and buti sinabihan mo agad ako noon. Alam ko naman na nag change ka na ng phone, pero still,
				good memories yung nakuha ko noon.
			</article>
		</div>
	</Modal>
	{:else if letterContent === 'Birthday'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Birthday letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: | Letter written: </p>
		<div class="overflow-y-auto">
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
		</div>
	</Modal>
	{:else if letterContent === 'Graduation'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Graduation letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: | Letter written: </p>
		<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
		Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
		Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
		<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
		Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
		Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
	</Modal>
	{/if}
</div>
<hr/>
<!-- //! birthday letter drafting will start by 2nd week of Oct. or Nov. Will be confidential once drafting starts. -->
<!-- //! Letter to be written ~ 2 weeks before Dec. 9. Dates may change w/o notice -->
<div class="blur-lg">
	<h1 class="m-5 mb-5 text-center">Graduation letter</h1>
	<div class="cheatline text-center">Letter finished: | Letter written: </div>
	<article class="m-10 mb-3">
		CONGRATULATIONS MY KAT KATTTT!!!! Wala pa ha? Test pa lang to. <br/>
	
		Katrina Clarisse B. Cabrera | Batch 2025 <br/>
		Bachelor of Science in Tourism Management <br/>
		Cum Laude
	</article>
	<footer class="m-10 mr-18 text-end">
		From your not related brother, personal photographer, supporter, guide, teacher, and close friend, <br />
		Hanz
	</footer>
</div>
<!-- 3rd letter end -->
<hr/>
<!-- 2nd letter start -->
 <div class="blur-lg">
	<h1 class="m-5 mb-5 text-center">Birthday letter</h1>
	<div class="cheatline text-center">Letter finished:  Month DD, 2024 | Letter written: Month DD, 2024</div>
	<article class="m-10 mb-3">
		Hai Kat Kattt, Happy 22nd birthday!!! Grabe no, wala pang 1 year pero close na close na tayo. Tamang bardagulan and whatever na want mo na gawin na kasama ako/kami, naging
		comfy ka ba naman eh. At least happy ka diba? yan ang important.
	</article>
	<footer class="m-10 mr-18 text-end">
		From your not related brother, personal photographer, and close friend, <br />
		Hanz
	</footer>
 </div>
<!-- 2nd letter end -->
<hr/>
<!-- 1st letter start -->

<h1 class="m-5 mb-5 text-center" bind:this={targetScroll}>Hello, Kat Kat.</h1>
<div class="cheatline text-center">Letter finished: October 9, 2024</div>
<article class="m-10 mb-3 text-center">
	Please access this page, <button class="cursor-pointer underline" on:click={() => goto(base + '/ToTheOnes')}>to my second circle.</button>
</article>
<footer class="m-10 mr-18 text-center">
	From the developer.
</footer>
<!-- placeholder letter end -->
<hr/>
<!-- 1st letter start -->
<h1 class="m-5 mb-5 text-center">Gratitude letter</h1>
<div class="cheatline text-center">Letter finished: June 10, 2024 | Letter written: June 11, 2024 | Letter updated: July 16, 2024</div>
<article class="m-10 mb-3">
	Hai Kat Kattt, mag thank u lang ako sa mga memories na nagawa natin together and sa kung saan pa.
	Alam mo, mamimiss kita ng sobra sobra. Kase araw araw ako pumapasok tas araw araw din kita
	nakikita. Tapos kung want mo magphotoshoot, ginagawa naman natin. Hindi lang dahil sa crush kita
	and what not, dahil sa malapit kita na kaibigan and syempre, memories mo na din yon sa school pag
	nakagraduate ka na. Thank you dahil sa naging inspiration and motivation kita! Alam mo naman na kung bakit kita nagustuhan eh.
  	Pero sabihin ko ulit, Maganda ka, mag ka-vibes tayo, same tayo ng music taste, hindi ka naninigarilyo, and syempre mabait ka.
</article>
<article class="m-10">
	Sana talaga maging Cum Laude graduate ka. I'm rooting for you beh. Palagi mo tandaan na nandito
	ako para sayo, kahit anong mangyari. Nakakatuwa din na naging close friend kita. Ang saya kase ng
	usapan natin palagi eh, tamang VMs, purong kapakshitan (AMEX PLATINUM, GALVANIZED SQUARE STEEL), tas sa mga
	nanggugulo sayo. Ang saya mo talaga kausap Kat Kat. To be honest beh, ikaw yung isa sa mga tao na
	ginawang bearable ang internship ko dahil sa kayo yung nilalapitan ko about doon. Rant dito about
	sa pinapagawa, rant doon sa kasabay ko, you get the point naman. Thank you, kase available ka
	kausapin if mag rant ako or chismis or what not. Sana ganon ka din in the future, pero if
	sasabihin mo na busy ka, hindi naman kita pipilitin. Basta mailahad ko lang yung want ko sabihin,
	masaya na ako. As long na nabasa mo. Tsaka next time, 'wag na kayong mag-away na magkapatid nang basta-basta.
  	Nahirapan ako na ikalma kayong pareho noon eh. Pero if ever na mangyari ulit yon, kahit ako ulit ang gawin niyong mediator.
  	Wala ako problem doon. Basta na ako lang ang mediator niyo.
</article>
<article class="m-10">
  	Sorry sa mga times na nagiging needy ako sa replies mo kahit alam ko na busy ka ng sobra and sa times na
  	hindi kita natutulungan sa schoolworks or sa pagbigay ng advice during rants mo kase nablangko utak ko. 
  	Tsaka pala, if need mo ng kausap about sa life or schoolworks
	or kung ano man yan, I'm here for you. Alam mo yan beh. Kahit na kausap ko kapatid mo about sa rants niya, kinakausap pa din kita about sa rants mo.
	Tsaka yung sa photoshoots natin, ang saya din non. Why? kase ikaw yung una ko naging personal
	model/subject sa mga photoshoots. Tsaka ang dami na din natin na photoshoots ah (3 or 5 na ata).
	Hindi mo pa naman nasasakop ng pictures mo yung SD card kaya safe ka pa. If want mo mag photoshoot, sabihan mo lang ako, alam ko naman na want mo din eh.
  	Sasabihan naman kita kung free ako. Tsaka mag photoshoot/gala tayo minsan beh, pwedeng tayo lang dalawa or kasama si Asli, si Fem, or kung sino pa na want mo isama.
  	Tsaka eto, 'wag mo isipin problems mo sa life as much as possible. Mag focus ka sa studies mo pa. Tignan mo ilang semesters
	na lang, tapos ka na. May latin honors pa. Sana talaga Kat na makatapos ka with latin honors. Like
	I said kanina, I'm rooting for you and I'll support you every step of the way.
</article>
<article class="m-10">
	I'm so thankful na nakilala kita Kat Kat, actually thankful ako sa inyong magkapatid. Ang ganda ng pinagsamahan natin kahit nung January lang
	tayo nag start na mag usap. So yun nga beh, thank you again sa mga memories, bondings, and for
	being my inspiration and motivation for this last semester. Mahal na mahal kita Kat. Pareho ko kayong mahal magkapatid. God bless u
	and ingat ka palagi. To more memories with u!!!
</article>
<footer class="m-10 mr-18 text-end">
	From your personal photographer and close friend, <br />
	Hanz
</footer>
<article class="m-10">
	P.S. Hindi ko makakalimutan yung time na nagmadali ako na umalis para lang kunin yung phone mo sa school. Umiiyak ka pa non tas pinapakalma pa kita habang nagmamadali aq magbike.
	Mystery adventure ba naman eh. Pero hey, hindi naman ako nagalit nung time na yon and buti sinabihan mo agad ako noon. Alam ko naman na nag change ka na ng phone, pero still,
	good memories yung nakuha ko noon.
</article>
<hr />
    
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Katrina/Kat Kat" required>
	</div>
	<div class="flex justify-center">
		 <textarea name="message" placeholder="Message" class="border rounded-lg inputColor p-1" required></textarea>
		 <button type="submit" value="Send" class="border rounded-lg p-2 mt-auto mb-auto ml-5 buttonChange">send</button>
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
		.buttonChange
		{margin-right: 12px;}
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
