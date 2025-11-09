<script>
// @ts-nocheck

	// import PE from '$lib/assets/TM/E.jpg?url';
	// import PE2 from '$lib/assets/TM/E2.jpg?url';
	// import PE3 from '$lib/assets/TM/E3.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let showModal = false;
	let letterContent = '';
	let userCheck = '';
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
		// Page non-accessible to others. Only to the developer.
		let hasItem;
		let valueCheck;
		onMount(async () => {
			hasItem = localStorage.getItem('letterKey') !== null;
			valueCheck = localStorage.getItem('letterKey');
			// Conditional logic based on hasItem
			// if (hasItem && valueCheck == import.meta.env.VITE_TM_26_T) {
			// } else {
			// 	goto(base + '/');
			// }
			if (hasItem && valueCheck == import.meta.env.VITE_SiteKey) {
			} else {
				goto(base + '/');
			}
			return userCheck = localStorage.getItem('letterKey');
		});
	}
</script>

{#if userCheck == import.meta.env.VITE_TM_26_T}
<title>TM/TM-26</title>
<div class="text-center m-5">Welcome, Pagulayan, E.</div>
{:else if userCheck == import.meta.env.VITE_SiteKey}
<title>Hello Developer.</title>
<div class="text-center m-5">Welcome, Lizaso, H. This is now hidden from her.</div>
{/if}
<div class="cheatline text-center">Page updated: November 3, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<!-- <img src={PE2} alt="N/A" class="object-cover mt-5 h-[300px] w-[500px] rounded-lg" /> -->
</header>
<hr/>
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">
		Please select the letter that you want to read.
	</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<!-- img={PE} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Gratitude letter</h5>
		  <p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
		  <Button class="bg-bgBlackWhite border border-[#dddddd] hover:bg-[#dddddd]" on:click={()=>(letterShow('Gratitude'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<!-- img={PE3} -->
		<Card  reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">To my 2nd circle</h5>
			<p class="mb-3 font-normal leading-tight">Access to cartas secreta.</p>
		  <Button class="bg-bgBlackWhite border border-[#dddddd] hover:bg-[#dddddd]" on:click={()=>(letterShow('Reminder'))}>
			Open letter
		  </Button>
		</Card>
	</div>
</div>
{#if letterContent === 'Gratitude'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: June 13, 2024 | Letter written: June 14, 2024</p>
		<div class="text-[#f5f3f3]">
			<!-- //* you may add carousel or images in between -->
			<article class="m-5">
				Hai Fem, thank you sa mga memories and sa bondings natin. Oo, ang dami nating pinagsamahan (konti lang pero hey, at least meron).
				So yun nga, fun fact, kung si Jovy yung main reason kung bakit ko kayo naging close, ikaw naman yung reason kung bakit ko naging close
				si Kat at Ash. Ikaw ba naman kase closest friend sa kanila eh. Kaya thank u for that.
			</article>
			<article class="m-5">
				Update about sa life ko kahit alam mo na,
				wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit (alam mo naman na kung bakit), 
				and naghahanap na trabaho. Yes nagpupuyat pa din pero di na masyado (well, pinagpuyatan ko tong pag draft ng letters).
				Grabe din ha, ikaw yung naging bridge ko sa magkapatid then for some reason, naging close friends ko sila then soon after, kayo nila Jovy then
				after that naman, nabuo na yung 2nd circle ko ulit. So dalawa kayo ni Jovy yung founding mothers ng new 2nd circle ko (Wao founding mothers damn).
				Yung gusto ko sa atin is yung asaran eh. Napakarandom mo mang asar, tapos minsan ang mga biro mo, napakalaswa HSHAHA napakalala mo talagang bata ka.
				Syempre na gustuhan mo yung regalo ko sayo nung birthday mo, which is yung photoshoot nga. Kita mo yung pic mo dito is galing doon.
				Then syempre, grateful ako na nakilala kita, hindi kita makikilala kung hindi dahil ka Jovy and sa event last October which is yung Mental Health Week.
				Buti na lang talaga beh.
			</article>
			<article class="m-5">
				I'm so thankful na nakilala kita Fem, mamimiss ko talaga yung memories and bondings natin and thankful talaga ako sayo, dahil sa nakilala kita and sa nakilala ko ang magkapatid. 
				Ang ganda ng pinagsamahan natin since last sem (mga random photoshoots, tamang asaran, tamang chismisan). 
				So yun nga beh, thank you again sa mga memories, kakulitan, and bondings natin! Mahal na mahal kita Fem. Thank you for being the foundation ng 2nd circle! God bless u, 
				ingat ka palagi, see u when I see u, and thank u ulit! To more memories with u!!!
			</article>
			<footer class="m-5 text-end">
				From your photographer and close friend, <br />
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

<hr />
    
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Fem" required>
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
		img {
			width: 77%;
		}
		.buttonChange
		{margin-right: 12px;}
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
