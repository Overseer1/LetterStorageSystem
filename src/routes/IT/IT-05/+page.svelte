<script>
// @ts-nocheck

	import EKJ from '$lib/assets/ITCS/KJ.jpg?url';
	import EKJ2 from '$lib/assets/ITCS/KJ2.jpg?url';
	import EKJ3 from '$lib/assets/ITCS/KJ3.jpg?url';
	import EKJ4 from '$lib/assets/ITCS/KJ4.jpg?url';
	import EKJ5 from '$lib/assets/ITCS/KJ5.jpg?url';
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
			if (hasItem && valueCheck == import.meta.env.VITE_IT_05_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>IT/IT-05</title>
<div class="text-center m-5">Welcome, Estipona, K.</div>
<div class="cheatline text-center">Page updated: November 3, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={EKJ2} alt="N/A" class="object-cover mt-5 h-[400px] w-[250px] rounded-lg" />
</header>
<hr/>
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">
		Please select the letter that you want to read.
	</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={EKJ} reverse={false} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Gratitude letter</h5>
		  <p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
		  <Button class="bg-bgGreen border border-[#059142] hover:bg-[#059142]" on:click={()=>(letterShow('Gratitude'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={EKJ3} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">To my 2nd circle</h5>
			<p class="mb-3 font-normal leading-tight">Access to cartas secreta.</p>
		  <Button class="bg-bgGreen border border-[#059142] hover:bg-[#059142]" on:click={()=>(letterShow('Reminder'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={EKJ5} reverse={false} class="bg-current text-[#f5f3f3]">
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Being drafted</h5>
			<p class="mb-3 font-normal leading-tight">Draft is hidden as per your request and mine.</p>
		  <Button class="bg-bgGreen border border-[#059142] hover:bg-[#059142]" on:click={()=>(letterShow('Graduation'))}>
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
			<article class="m-5">
				Hai Tin, thank u sa mga memories and bondings natin. Mamimiss q yung random pitch sales mo sa akin tsaka
				yung minsanan na rant q sayo. Tas kung minsan, nag bibigay ka advice sa akin dahil sa mga pinaggagawa ko before
				(attempted na ano sa life). Dahil dyan, bibigyan kita update sa life, wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit (alam mo naman na kung bakit), 
				and naghahanap na trabaho.
			</article>
			<article class="m-5">
				Yes nagpupuyat pa din pero di na masyado (well, pinagpuyatan ko tong pag draft ng letters) and rarely na nakakaisip ng no good pero no, I won't do it na kase na open na eyes ko sa mangyayari.
				Thank u sa mga advices mo and yun nga, sa mga pitch sales mo. Yes, sinusunod ko naman advice mo (from time to time) and yes, natutuwa ako sa mga pitch sales mo minsan.
				Kung iniisip mo kung ano yung pitch sales na tinutukoy ko, well yun yung times na sinasabi mo na bumili ako ng pagkain and/or drinks sayo (e.g. Mango Tapioca, Graham Balls).
				Galing mo din eh, nacoconvince mo q na bumili kaya ayun, may maneh ka na at may food aq. Good trade naman yon. Tsaka eto pa, mamimiss q random photoshoots natin, kagaya ng nandito sa page ngayon at yung
				1x1 mo para sa CV mo sa capstone docu (ata nakalimutan q na yon). Syempre thankful aq na nakilala at naging close friend kita. Kagaya nga ng sinabi ko kanina, naging advisor kita kaya ayun.
			</article>
			<article class="m-5">
				I'm so thankful na nakilala kita Tin, mamimiss ko talaga yung memories and bondings natin and
				ang ganda ng pinagsamahan natin since last school year (mga random photoshoots, tamang asaran, tamang chismisan). 
				So yun nga beh, thank you again sa mga memories, kakulitan, and bondings natin! Mahal na mahal kita Tin. God bless u, 
				ingat ka palagi, see u when I see u, and thank u ulit! To more memories with u!!!
			</article>
			<footer class="m-5 text-end">
				From your photographer, customer, and close friend, <br />
				Hanzyboy
			</footer>
			
		</div>
	</Modal>
{:else if letterContent === 'Reminder'}
<Modal bind:showModal>
	<h2 slot="letterType" class="text-white text-xl cheatline text-center">
		Graduation letter
	</h2>
	<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
		Draft Started: 2025 | Letter finished: 2025 | Letter written: 2025
	</h3>
	<div class="text-[#f5f3f3]">
		<article class="m-5">
			Please access this page, <button class="cursor-pointer underline" on:click={() => goto(base + '/ToTheOnes')}>to my second circle.</button>
		</article>
		<footer class="m-5 text-end">
			From the developer.
		</footer>
	</div>
</Modal>
{:else if letterContent === 'Graduation'}
<Modal bind:showModal>
	<h2 slot="letterType" class="text-white text-xl cheatline text-center">
		Graduation letter
	</h2>
	<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">
		Draft Started: 2025 | Letter finished: 2025 | Letter written: 2025
	</h3>
	<div class="text-[#f5f3f3]">
		<article class="m-5">
			CONGRATULATIONS MY TIN TINNNNN!!!! //multiple additionals for letter | helping and 
			supporting<br />
		</article>
		<article class="m-5"></article>
		<article class="m-5">
			Kristine Joy G. Estipona | Batch 2025 <br />
			Bachelor of Science in Information Technology <br />
			//Cum Laude
		</article>
		<footer class="m-5 text-end">
			From your not related brother, personal photographer, supporter, guide, teacher, and
			close friend, <br />
			Hanz
		</footer>
	</div>
</Modal>
{/if}

<hr />
    
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Tin Tin" required>
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
		background-color: #059142;
		color: #f5f3f3;
	}
	:global(html) {
		background-color: theme(colors.bgGreen);
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
