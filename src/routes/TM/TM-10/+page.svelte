<script>
// @ts-nocheck

	import MJ from '$lib/assets/TM/J.jpg?url';
	import MJB from '$lib/assets/TM/J1.webp?url';
	import MJ2 from '$lib/assets/TM/J2.jpg?url';
	import MJ3 from '$lib/assets/TM/J3.jpg?url';
	import MJ4 from '$lib/assets/TM/J4.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let showModal = false;
	let letterContent = '';
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
			// Conditional logic based on hasItem
			if (hasItem && valueCheck == import.meta.env.VITE_TM_10_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>TM/TM-10</title>
<div class="text-center m-5">Welcome, Margate, J.</div>
<div class="cheatline text-center">Page updated: November 3, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={MJ} alt="N/A" class="object-cover mt-5 h-[250px] w-[450px] rounded-lg imgHead" />
</header>
<hr/>
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">
		Please select the letter that you want to read.
	</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MJ3} reverse={false} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Gratitude letter</h5>
		  <p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
		  <Button class="bg-bgRoseGold border border-[#b76e79] hover:bg-[#b76e79]" on:click={()=>(letterShow('Gratitude'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MJ4} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">To my 2nd circle</h5>
			<p class="mb-3 font-normal leading-tight">Access to cartas secreta.</p>
		  <Button class="bg-bgRoseGold border border-[#b76e79] hover:bg-[#b76e79]" on:click={()=>(letterShow('Reminder'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MJ2} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Birthday letter</h5>
		  <p class="mb-3 font-normal leading-tight">Happy 20th birthday mi hija, hermana, bff, and model!!!</p>
		  <Button class="bg-bgRoseGold border border-[#b76e79] hover:bg-[#b76e79]" on:click={()=>(letterShow('Birthday'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	{#if letterContent === 'Gratitude'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: June 13, 2024 | Letter written: June 14, 2024 | Letter updated: July 04, 2024</p>
		<div class="text-[#f5f3f3]">
			<!-- //* you may add carousel or images in between -->
			<article class="m-5">
				Hai Jovy/Anakis, thank u for the memories and bonding sa life and sa school. Mamimiss q yon and yung mga random photoshoots natin.
				Oo, kaya pa ng camera ko pagmumukha mo kase sabi ko. Himala nga na kaya pa eh.
				Alam mo naman na current status ko sa life, wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit, 
				and naghahanap na trabaho. Yes nagpupuyat pa din pero di na masyado (well, pinagpuyatan ko tong pag draft ng letters).
			</article>
			<article class="m-5">
				So yun nga no, thankful ako na kilala kita. Why? kase ikaw ang reason kung paano ko nakilala ang magkapatid at si Fem. Ikaw ang reason kung bakit
				nabuo ulit yung 2nd circle ko. Kayo yung pumalit sa mga former members noon and I'm proud. Isipin mo yon, ikaw yung naging reason sa reformation
				ng 2nd circle ko. Ang lupit no? Ikaw kase eh. Ang uniqueness lang ng 2nd circle is majority ay babae. Parang naging babaero ako doon ah, pero meh,
				at least kaibigan ko kayo and you all know it naman. Speaking of that, ang uniqueness sayo is yung bigla mo akong ginawang tatay. Ewan q kung bakit mo naisip 
				yon pero sige, you do you girl. Tsaka eto pala, thank you at tumulong ka sa hide and seek natin nung nahimatay ako. Inalalayan mo pa nga ako eh, kaso na kay
				Marielle yung bigat HSHAHA tas nag domino effect pa. Alam ko na say ko na to sayo pero here oh, doon ko narealize kung gaano ko sila kaclose, kung gaano ko kayo kaclose, at kung anong klaseng pag aalaga ang binigay 
				niyo sa akin that day. Dahil doon, magiging reason ko yon if ever na magisip ako na tapusin ang life ko. Hindi naman na mangyayari yon ever again. Malaki ang utang na loob ko sa inyo. Thank you so much.
			</article>
			<article class="m-5">
				I'm so thankful na nakilala kita Jovy, mamimiss ko talaga yung memories and bondings natin and thankful talaga ako sa reformation ng 2nd circle dahil sayo. Ang ganda ng pinagsamahan natin since last sem
				(mga random photoshoots, tamang pag comfort sayo pag malungkot ka, inalalay mo aq nung May 30, tamang asaran, tamang chismisan). 
				So yun nga anakis, thank you again sa mga memories, kakulitan, and bondings natin! Mahal na mahal kita anakis. Thank you for being the foundation ng 2nd circle! God bless u, 
				ingat ka palagi, see u when I see u, and thank u ulit! To more memories with u!!!
			</article>
			<footer class="m-5 text-end">
				From your school father, photographer, and close friend, <br />
				Hanz
			</footer>
			<article class="m-5">
				P.S. Oo alam ko na aalis ka na soon kaya nilagay ko na dito yung leave a message. Ikaw na bahala kung gagamitin mo or not, pero please keep in touch ha? Yun lang naman, ingat ka
				palagi and love u so mats!
			</article>
		</div>
	</Modal>
	{:else if letterContent === 'Birthday'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Birthday letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: October 15, 2024</p>
		<div class="text-[#f5f3f3]">
			<div class="flex justify-center">
				<img src={MJB} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" />
			</div>
			<article class="m-5">
				Hai Jovy, HAPPY 20TH BIRTHDAY SAYO MI ANAKISSS!!! or HAPPY 20TH BIRTHDAY SAYO MY FOUNDING MOTHER!!! Sorry kung eto lang regalo ko, yung picture naman na naka layout is gawa ko naman kaya ayan lang muna ha? Anw, dahil ikaw ay 20 na, dapat maging maayos ang decisions and/or choices mo sa life and of course, nandito lang kami for you.
				Tandaan mo palagi yon ha? Nandito lang ako, si Kat Kat, si Asli, si Marielle, at kung sino pa para supportahan, samahan, tulungan, at pakinggan ka. Oki? Ano pa ba, well namimiss ko na random photoshoots natin. 
				Aminin natin na mas madami photoshoots ni Kat Kat at ni Asli, pero kulang pics mo dito aba. Dapat madami to eh, so dapat makapag photoshoot tayo soon. Feel ko need mo malaman to kahit alam na alam mo na to, so eto,
				mahal na mahal ka namin, as in. Kahit alam mo na yan, sabihin mo na lang na reminder lang yon. So ayun. Sana nasa mabuting kalagayan ka ngayon and mag ingat ka palagi ha? Miss na miss ka na namin or should I say, 
				MISS NA MISS NA KITA!!! Sana talaga magkita tayo soon. Of course, sorry kung minsan napapaoverthink kita and sa kung ano pang bad things. I'm really sorry anak. I wish you all the best girl, do your best lang ha? Proud na proud ako sayo kahit malayo ako sayo. Uulitin ko, nandito lang ako/kami for you ha?
				I love you so fucking much Jovy, Alam mo yon. I'm so thankful for you mi hija. Ikaw nag link sa amin ni Kat Kat at Asli, naging founding mother (wao) ng 2nd circle ko, and syempre, naging kaibigan kita, tas malapit pa. It's beautiful. 
				Nakakamiss ka sobra. Baka maiyak pa tayong dalawa pag nagkita tayo ulit. Do me a favor, grumaduate ka ng may Latin Honors. Si Kat Kat ang unang kaibigan natin na magiging Cum Laude, dapat ikaw din at yung iba ay Cum Laude. Okay lang kung hindi, at least ginawa niyo best niyo. I know that and I'm proud of you for doing your best. 
				See u soonest, God bless you, and to more memories with you!!!
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
		<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: October 9, 2024</h3>
		<div class="text-[#f5f3f3]">
			<article class="m-5">
				Please access this page, <button class="cursor-pointer underline" on:click={() => goto(base + '/ToTheOnes')}>to my second circle.</button>
			</article>
			<footer class="m-5 text-end">
				From the developer.
			</footer>
		</div>
	</Modal>
	{/if}
</div>

<hr />
    
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Jovy/Anakis" required>
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
		.buttonChange
		{margin-right: 12px;}
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
