<script>
// @ts-nocheck

	import CKC from '$lib/assets/TM/KC.jpg?url';
	import CKC1 from '$lib/assets/TM/KC1.jpg?url';
	import CKC2 from '$lib/assets/TM/KC2.jpg?url';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let DevAcc = '';
	let DevPass = '';
	let DevOpt = false;
	let showImgs = false
	  const developerSide = () =>
	  {
		if (DevPass == import.meta.env.VITE_DevPass)
	  	{
			DevOpt = true
			alert('Welcome developer. Please turn off your screen sharing stream/s before proceeding.')
	  	}
		else if (DevPass == import.meta.env.VITE_DevPassImg)
	  	{
			showImgs = true
			alert('Thank you. The changes you will only see are the pictures selected by the developer.')
	  	}
		else
		{
			alert('Wrong password.')
		}
	  }
	  const LogOut = () =>
	  {
			DevAcc = false
			DevPass = false
			DevOpt = false
			alert("Thank you. Progress has been saved.");
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
			if (hasItem && valueCheck == 'TM-KC') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>TM/TM-KC</title>
<div class="text-center m-5">Welcome, Cabrera, K. C.</div>
<div class="cheatline text-center">Page updated: October 9, 2024</div>
{#if DevOpt == true || showImgs == true}
<header class="overflow-hidden mb-5 flex justify-center">
	<!-- //! 3 pictures will be set, pictures can be changed or retained -->
	<img src={CKC} alt="N/A" class="object-cover mt-5 h-[250px] w-[450px] mr-10 rounded-lg" />
	<img src={CKC2} alt="N/A" class="object-cover mt-5 h-[250px] w-[450px] mr-10 rounded-lg" />
	<img src={CKC1} alt="N/A" class="object-cover mt-5 h-[250px] w-[450px]  rounded-lg" />
</header>
{:else}
<header class="overflow-hidden mb-5 flex justify-center">
	<!-- //! 3 pictures will be set, pictures can be changed or retained -->
	<img src={CKC} alt="N/A" class="object-cover mt-5 h-[250px] w-[450px] mr-10 rounded-lg" />
</header>
{/if}
<hr/>

<!-- //! birthday letter drafting will start by 2nd week of Oct. or Nov. Will be confidential once drafting starts. -->
<!-- //! Letter to be written ~ 2 weeks before Dec. 9. Dates may change w/o notice -->
{#if DevOpt == true}
<h1 class="m-5 mb-5 text-center">Graduation letter</h1>
<div class="cheatline text-center">Letter finished: | Letter written: </div>
<article class="m-10 mb-3">
	CONGRATULATIONS MY KAT KATTTT!!!! Wala pa ha? Test pa lang to.

	Katrina Clarisse B. Cabrera | Batch 2025
	Bachelor of Science in Tourism Management
	Cum Laude
</article>
<footer class="m-10 mr-18 text-end">
	From your not related brother, personal photographer, supporter, guide, teacher, and close friend, <br />
	Hanz
</footer>
<!-- 3rd letter end -->
<hr/>
<!-- 2nd letter start -->
<h1 class="m-5 mb-5 text-center">Birthday letter</h1>
<div class="cheatline text-center">Letter finished:  Month DD, 2024 | Letter written: Month DD, 2024</div>
<article class="m-10 mb-3">
	Hai Kat Kattt, Happy 22nd birthday sayo! Wala pa ha? Test pa lang to.
</article>
<footer class="m-10 mr-18 text-end">
	From your not related brother, personal photographer, and close friend, <br />
	Hanz
</footer>
<!-- 2nd letter end -->
<hr/>
<!-- 1st letter start -->
{/if}
<h1 class="m-5 mb-5 text-center">Hello, Kat Kat.</h1>
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
<div class="flex justify-center">
	<input type="checkbox" bind:checked={DevAcc} hidden={DevOpt}/>
	<!-- svelte-ignore a11y-label-has-associated-control -->
	<label hidden={DevAcc}>Dev access only</label>
	<form on:submit|preventDefault={developerSide} hidden={!DevAcc}>
		{#if DevOpt == false}
		<input type="password" placeholder="Developer's password" class=" border rounded-lg text-black m-4 p-1 inputColor" bind:value={DevPass}>
		<button type="submit" value="Send" class="border rounded-lg p-2 mt-auto mb-auto ml-5 buttonChange">Access</button>
		{/if}
	</form>
	{#if DevOpt == true}
	<button on:click={LogOut} class="border rounded-lg p-2 mt-auto mb-auto ml-5 buttonChange">Log out</button>
	{/if}
</div>

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
		color: #dddddd;
	}
	@media screen and (max-width: 700px) {
		img {
			width: 77%;
		}
		.buttonChange
		{margin-right: 12px;}
		/* partial implementation only */
		header
		{
			display: block;
			height: auto;
			width: auto;
			margin-left:120px;
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
