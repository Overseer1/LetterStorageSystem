<script>
// @ts-nocheck
	import cartas from '../letterHolderIT.json'
	import EKJ from '$lib/assets/ITCS/KJ0.jpg?url';
	import EKJ2 from '$lib/assets/ITCS/KJ02.jpg?url';
	import EKJ3 from '$lib/assets/ITCS/KJ03.jpg?url';
	import EKJ4 from '$lib/assets/ITCS/KJ04.jpg?url';
	import EKJ5 from '$lib/assets/ITCS/KJ5.jpg?url';
	import EKJ6 from '$lib/assets/ITCS/KJ6.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let showModal = false;
	let letterContent = '';
	const gratitudeFooter = cartas.IT05.Gratitude.Footer.replace(/\n/g, '<br />');
	const graduationHeader = cartas.IT05.Graduation.Header.replace(/\n/g, '<br />');
	const graduationFooter = cartas.IT05.Graduation.Footer.replace(/\n/g, '<br />');
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
			if (hasItem && valueCheck == import.meta.env.VITE_IT_05_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>Hai, Tin Tinnnnn</title>
<div class="text-center m-5">Welcome, Estipona, K.</div>
<div class="cheatline text-center">Page updated: July 10, 2025</div>
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
			<h5 class="mb-2 text-2xl font-bold tracking-tight">Graduation letter</h5>
			<p class="mb-3 font-normal leading-tight">Congratulations mi hermana!</p>
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
			<article class="m-5">
				{cartas.IT05.Gratitude.Section1}
			</article>
			<article class="m-5">
				{cartas.IT05.Gratitude.Section2}
			</article>
			<article class="m-5">
				{cartas.IT05.Gratitude.Section3}
			</article>
			<footer class="m-5 text-end">
				{@html gratitudeFooter}
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
		Draft Started: June 10, 2025 | Letter finished: July 9, 2025 | Letter written: July 10, 2025
	</h3>
	<div class="flex justify-center">
				<img src={EKJ6} alt="N/A" class="object-cover mt-5 h-[300px] w-[250px] rounded-lg" />
			</div>
	<div class="text-[#f5f3f3]">
		<article class="m-5">
			{@html graduationHeader}
		</article>
		<article class="m-5">
			{cartas.IT05.Graduation.Section1}
		</article>
		<article class="m-5">
			{cartas.IT05.Graduation.Section2}
		</article>
		<article class="m-5">
			{cartas.IT05.Graduation.Section3}
		</article>
		<footer class="m-5 text-end">
			{@html graduationFooter}
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
