<script>
// @ts-nocheck
	import cartas from '../letterHolderNTS.json';
	import GQ from '$lib/assets/NTS/GA-Q01.jpg?url';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	const gratitudeFooter = cartas.GA15.Footer.replace(/\n/g, '<br />');
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
			if (hasItem && valueCheck == import.meta.env.VITE_GA_15_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>NTS/GA-15</title>
<div class="text-center m-5">Welcome, Ms. Gregorio, Q.</div>
<div class="cheatline text-center">Letter finished: June 10, 2024 | Letter written: June 13, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={GQ} alt="N/A" class="object-cover mt-10 h-[260px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	{cartas.GA15.Section1}
</article>
<article class="m-10">
	{cartas.GA15.Section2}
</article>
<article class="m-10">
	{cartas.GA15.Section3}
</article>

<footer class="m-10 mr-18 text-end">
	{@html gratitudeFooter}
</footer>

<hr />
    
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Ma'am Quinnah" required>
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
