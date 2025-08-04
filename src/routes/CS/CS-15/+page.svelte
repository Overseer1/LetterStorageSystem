<script>
// @ts-nocheck

	import MMK from '$lib/assets/ITCS/MK.jpg?url';
	import MMK2 from '$lib/assets/ITCS/MK2.jpg?url';
	import MMK3 from '$lib/assets/ITCS/MK3.jpg?url';
	import MMK4 from '$lib/assets/ITCS/MK4.jpg?url';
	import MMK5 from '$lib/assets/ITCS/MK5.jpg?url';
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
			if (hasItem && valueCheck == import.meta.env.VITE_CS_15_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>CS/CS-15</title>
<div class="text-center m-5">Welcome, Marson, M. K.</div>
<div class="cheatline text-center">Page updated: November 3, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={MMK} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" />
</header>
<hr/>
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">
		Please select the letter that you want to read.
	</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MMK3} reverse={false} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Gratitude letter</h5>
		  <p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
		  <Button class="bg-bgPink border border-[#fd5da8] hover:bg-[#fd5da8]" on:click={()=>(letterShow('Gratitude'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MMK4} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Birthday letter</h5>
		  <p class="mb-3 font-normal leading-tight">Happy 22nd birthday mi hija, hermana, bff, and model!!!</p>
		  <Button class="bg-bgPink border border-[#fd5da8] hover:bg-[#fd5da8]" on:click={()=>(letterShow('Birthday'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={MMK2} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">To my 2nd circle</h5>
			<p class="mb-3 font-normal leading-tight">Access to cartas secreta.</p>
		  <Button class="bg-bgPink border border-[#fd5da8] hover:bg-[#fd5da8]" on:click={()=>(letterShow('Reminder'))}>
			Open letter
		  </Button>
		</Card>
	</div>
</div>
<hr/>
{#if letterContent === 'Gratitude'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: June 17, 2024 | Letter written: June 17, 2024</p>
		<div class="text-[#f5f3f3]">
			<!-- //* you may add carousel or images in between -->
			<article class="m-10 mb-3">
				Hai Marielle, so ano no, bakit kita ginagawan ng letter eh inaaway mo q palagi. De ano, thank u sa mga memories and bondings
				natin. Tsaka sa mga katarantaduhan since last school year. Ewan ko kung kanino mo nakuha yung ugali na yan pero oks lang, gago din kami eh.
				Update about sa life ko kahit alam mo na,
				wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit (alam mo naman na kung bakit), 
				and naghahanap na trabaho. Yes nagpupuyat pa din pero di na masyado (well, pinagpuyatan ko tong pag draft ng letters).
			</article>
			<article class="m-10 mb-3 ">
				So yun nga, grabe pinagsamahan natin ah, lalo na yung nagpakitang gilas pa tayo nung intrams. Nahimatay ba naman tayo eh,
				tas nadamay pa natin si Ashley. Well, at least okay na tayong tatlo. Thankful ako kase tinulungan mo pa din ako kahit pagod ka na. 
				I owe you for that. Tsaka alam ko na sinabi ko na sayo to before, pero sasabihin ko ulit.
				Doon ko narealize kung gaano ko sila kaclose, kung gaano ko kayo kaclose, at kung anong klaseng pag aalaga ang binigay 
				niyo sa akin that day. Dahil doon, magiging reason ko yon if ever na magisip ako na tapusin ang life ko. Hindi naman na mangyayari yon ever again. Thank you talaga.
				Tsaka eto pa, buti ikaw yung co-photographer ko minsan. Enthusiastic ka kase pag may hawak ka na camera eh. Baka nga ikaw na maging photographer ng school eh
				(kung want mo lang). Tsaka ang lupit mo din manggisa ah. Konting gisa pa, maaamoy ko na yung chopsuey eh. Baka nga masunog mo pa.
			</article>
			<article class="m-10 mb-3">
				I'm so thankful na nakilala kita, mamimiss ko talaga yung memories and bondings natin and
				ang ganda ng pinagsamahan natin since last school year (mga random photoshoots, tamang asaran, tamang chismisan). 
				So yun nga beh, thank you again sa mga memories, kakulitan, and bondings natin! Mahal na mahal kita. God bless u, 
				ingat ka palagi, see u when I see u, and thank u ulit! To more memories with u!!!
			</article>
			<footer class="m-10 mr-18 text-end">
				From your school twin brother, co-photographer, and close friend, <br />
				Hanz
			</footer>
		</div>
	</Modal>
{:else if letterContent === 'Birthday'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Birthday letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: July 16, 2024</p>
		<div class="text-[#f5f3f3]">
			<article class="m-5">
				Hai Marielle, Happy birthday sayo! So napaka konti lang naman ng mensahe q sau. Ikaw ay maging maayos sa last 2 years ng college life mo. Malapit ka na din mag research.
				Hindi ko alam kung running ka for Cum Laude, pero galingan mo pa din ha? So yun nga, nasa letter naman na yung want ko sabihin sayo so ayun. God bless you and enjoy your day!!
				Ay wait, kung need mo ng kausap, nandito aq at sila, oki? oki, yun lang!
			</article>
			<footer class="m-5 text-end">
				From your school twin brother, co-photographer, and close friend, <br />
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
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Marielle" required>
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
		background-color: #fd5da8;
		color: #eeeeee;
	}
	:global(html) {
		background-color: theme(colors.bgPink);
		color: #dddddd;
	}
	@media screen and (max-width: 600px) {
		img {
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
