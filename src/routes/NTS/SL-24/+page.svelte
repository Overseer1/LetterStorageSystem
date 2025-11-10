<script>
// @ts-nocheck
	import cartas from '../letterHolderNTS.json';
	import RA from '$lib/assets/NTS/SL-A.jpg?url';
	import RA2 from '$lib/assets/NTS/SL-A02.jpg?url';
	import RA3 from '$lib/assets/NTS/SL-A03.jpg?url';
	import RA4 from '$lib/assets/NTS/SL-A04.jpg?url';
	import RA5 from '$lib/assets/NTS/SL-A05.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	let showModal = false;
	let letterContent = '';
	const gratitudeFooter = cartas.SL24.Gratitude.Footer.replace(/\n/g, '<br />');
	const teachersDayFooter = cartas.SL24.TeachersDay.Footer.replace(/\n/g, '<br />');
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
			if (hasItem && valueCheck == import.meta.env.VITE_SL_24_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>NTS/SL-24</title>
<div class="text-center m-5">Welcome, Mrs. Rosal, A.</div>
<div class="cheatline text-center">Page updated: November 3, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={RA} alt="N/A" class="object-cover mt-5 h-[270px] w-[450px] rounded-lg" />
</header>
<hr/>
<header class="overflow-hidden flex justify-center cheatline my-5">
	<p class="text-lg">
		Please select the letter that you want to read.
	</p>
</header>
<div class="flex justify-center max-sm:block">
	<div class="overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={RA2} reverse={false} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Gratitude letter</h5>
		  <p class="mb-3 font-normal leading-tight">A thank you letter before I leave my Alma Mater.</p>
		  <Button class="bg-bgPurp border border-[#6d28d9] hover:bg-[#6d28d9]" on:click={()=>(letterShow('Gratitude'))}>
			Open letter
		  </Button>
		</Card>
	</div>
	<div class="overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={RA3} reverse={false} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Teacher's day letter</h5>
		  <p class="mb-3 font-normal leading-tight">A thank you letter to our second mother.</p>
		  <Button class="bg-bgPurp border border-[#6d28d9] hover:bg-[#6d28d9]" on:click={()=>(letterShow('TeacherDay'))}>
			Open letter
		  </Button>
		</Card>
	</div>
</div>
{#if letterContent === 'Gratitude'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
		<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: June 13, 2024 | Letter written: June 13, 2024</h3>
		<div class="text-[#f5f3f3]">
			<!-- //* you may add carousel or images in between -->
			<article class="m-5">
				{cartas.SL24.Gratitude.Section1}
			</article>
			<article class="m-5">
				{cartas.SL24.Gratitude.Section2}
			</article>
			<article class="m-5">
				{cartas.SL24.Gratitude.Section3}
			</article>
			<footer class="m-5 text-end">
				{@html gratitudeFooter}
			</footer>			
		</div>
	</Modal>
{:else if letterContent === 'TeacherDay'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Teacher's day letter</h2>
		<h3 slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: October 4, 2024</h3>
		<div class="flex justify-center">
			<img src={RA4} alt="N/A" class="object-cover mt-10 h-[270px] w-[450px] rounded-lg" />
		</div>
		<div class="text-[#f5f3f3]">
			<article class="m-5">
				{cartas.SL24.TeachersDay.Section1}
			</article>
			<footer class="m-5 text-end">
				{@html teachersDayFooter}
			</footer>
		</div>
		<div class="flex justify-center">
			<img src={RA5} alt="N/A" class="object-cover mt-5 h-[270px] w-[450px] rounded-lg" />
		</div>
	</Modal>
{/if}

<hr />
    
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Ma'am Anna" required>
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
	:global(html) {
		background-color: theme(colors.bgPurp);
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
