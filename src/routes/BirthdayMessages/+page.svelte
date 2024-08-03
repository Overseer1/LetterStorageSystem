<script>
    // @ts-nocheck
        import { goto } from '$app/navigation';
        import { onMount } from 'svelte';
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
<title>Message for the dev</title>
<div class="text-center m-5">Welcome</div>
<div class="cheatline text-center">‎ </div>
<div class="text-center mt-40 mb-12 mr-2 ml-2">Today is the developer's birthday! If you want, you may leave a message to the developer.</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" required>
	</div>
	<div class="flex justify-center">
		 <textarea name="message" placeholder="Message" class="border rounded-lg inputColor p-1" required></textarea>
		 <button type="submit" value="Send" class="border rounded-lg p-2 mt-auto mb-auto ml-5 buttonChange">send</button>
	</div>
</form>
<style lang="postcss">
	.cheatline {
		background-color: #ffeb3b;
		color: #313131;
	}
	:global(html) {
		/* background-color: theme(colors.bgPink); */
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
  	width: 600px;
  	height: 300px;
	}
	@media screen and (max-width: 500px) {
		textarea {
  		width: 500px;
  		height: 200px;
		margin: 15px;
		}
		
	}
</style>
