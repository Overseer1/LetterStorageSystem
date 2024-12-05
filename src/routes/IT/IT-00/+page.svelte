<script>
// @ts-nocheck

	import CKC from '$lib/assets/TM/KC.jpg?url';
	import CMA from '$lib/assets/TM/MA1.jpg?url';
	import CKC1 from '$lib/assets/TM/KC1.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	let showModal = false;
	let letterContent = '';
  	let vCard = false;
	function letterShow(contentSelect){
		letterContent = contentSelect;
		showModal = true;
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
			if (hasItem && valueCheck == import.meta.env.VITE_SiteKey) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>Developer's testbench</title>
<div class="text-center m-5">Welcome, Developer.</div>
<div class="cheatline text-center mb-5">‎</div>
<hr />
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-xl text-[#313131]">
		These are the current letters that are for writing.
	</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC1} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Birthday Letter</h5>
		  <p class="mb-3 font-normal leading-tight">For Cabrera, Katrina Clarisse</p>
		  <Button class="bg-bgBlue hover:bg-[#ffeb3b] hover:text-[#313131]" on:click={()=>(letterShow('Graduation'))}>
			Read more
		  </Button>
		</Card>
	</div>

	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CMA} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Birthday Letter</h5>
		  <p class="mb-3 font-normal leading-tight">For Cabrera, Marykate Ashley</p>
		  <Button class="bg-bgBlue hover:bg-[#ffeb3b] hover:text-[#313131]" on:click={()=>(letterShow('Birthday'))}>
			Read more
		  </Button>
		</Card>
	</div>
	
	<!-- <div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Letter type</h5>
		  <p class="mb-3 font-normal leading-tight">Letter summarization.</p>
		  <Button class="bg-bgBlue hover:bg-[#ffeb3b] hover:text-[#313131]" on:click={()=>(letterShow('Gratitude'))}>
			Read more
		  </Button>
		</Card>
	</div> -->
	{#if letterContent === 'Graduation'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-[#313131] text-xl cheatline text-center">Birthday letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: December 1, 2024 | Letter written: December 5, 2024</p>
		<h3 class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
			Letter to be shown by 10:00 PM of December 6.
		</h3>
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
				I'll still listen to you kahit late ako mag reply. Basta ichat mo lang yan, babasahin ko
				naman yan oki? I'm so grateful to God kase nakilala kita Kat Kat, nandiyan ka palagi for
				me, nakakapagrant tayo sa isa't isa para mapakalma natin ang sarili natin, nakakapagshare
				tayo ng kanta or memes, or anything na want natin, and syempre, magkavibes pa tayo.
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
		</div>
	</Modal>
	{:else if letterContent === 'Birthday'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-[#313131] text-xl cheatline text-center">Birthday letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: December 3, 2024 | Letter written: December 6, 2024</p>
		<h3 class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
			Letter to be shown by 10:00 PM of December 6.
		</h3>
		<div class="text-[#f5f3f3]">
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
	{:else if letterContent === 'Gratitude'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-[#313131] text-xl cheatline text-center">Letter type</h2>
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
<hr />
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>

<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" required>
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
		background-color: #ffeb3b;
	}
	.inputColor {
		color: #313131;
	}
	:global(html) {
		background-color: theme(colors.bgBlue);
		color: #dddddd;
	}
	@media screen and (max-width: 700px) {
		/* img {
			width: 77%;
		} */
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
