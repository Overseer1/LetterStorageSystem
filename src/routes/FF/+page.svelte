<script>
// @ts-nocheck
	import { goto } from '$app/navigation';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
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
</script>
<title>Final letter</title>
<div class="text-center m-5">Welcome, family member or friend</div>
<div class="cheatline text-center">Letter finished: July 05, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<!-- //!insert img if applicable -->
	<!-- <img src={//! insert import variable here} alt="N/A" class="object-cover mt-10 h-[260px] w-[450px] rounded-lg" /> -->
</header>
<article class="m-10 mb-3">
	Hello, family and friends. Thank you for the support and guidance. 
</article>
<footer class="m-10 mr-18 text-end">
	From your apo, pamangkin, pinsan, anak, and friend,<br />
	Hanz Edilberto O. Lizaso III, <br />
	Bachelor of Science in Information Technology,<br />
	Loyalty Awardee <br />
</footer>

<hr />

<div class="text-center mt-5">If you want, you may leave a message to the developer.</div>
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
		color: #313131;
	}
	.inputColor {
		color: #313131;
	}
	textarea {
  	width: 500px;
  	height: 200px;
	}
	:global(html) {
		background-color: theme(colors.bgBlue);
		color: #f5f3f3;
	}
	@media screen and (max-width: 600px) {
		img {
			width: 77%;
		}
		.buttonChange
		{margin-right: 12px;}
	}
	@media screen and (max-width: 500px) {
		textarea {
  		width: 500px;
  		height: 200px;
		margin: 15px;
		}
		
	}
</style>
