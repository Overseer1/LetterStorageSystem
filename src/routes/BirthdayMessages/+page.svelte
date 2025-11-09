<script>
    // @ts-nocheck
	 	import { Card, Button, Label, Input, Checkbox, Textarea } from "flowbite-svelte";
		import Icon from "@iconify/svelte";
        import { goto } from '$app/navigation';
        import { onMount } from 'svelte';
        import { base } from '$app/paths';
        import emailjs from '@emailjs/browser';
		let clearName, clearEmail, clearMessage;
          const sendEmail = (/** @type {{ target: string | HTMLFormElement; }} */ e) => {
            emailjs
              .sendForm(import.meta.env.VITE_EmailJS_ServiceID, import.meta.env.VITE_EmailJS_TemplateIDFF, e.target, {
                publicKey: import.meta.env.VITE_EmailJS_PublicKey,
              })
              .then(
                () => {
                  console.log('SUCCESS!');
                  alert("Message sent");
				  clearName = "";
				  clearEmail = "";
				  clearMessage = "";
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
<div class="text-center mt-12 mb-12 mr-2 ml-2">Today is the developer's birthday! If you want, you may leave a message to the developer.</div>
<div class="flex justify-center">
	<Card class="p-4 sm:p-6 md:p-8">
  <form class="flex flex-col space-y-6" on:submit|preventDefault={sendEmail}>
    <h3 class="text-xl font-medium text-gray-900 dark:text-white">Write your message here</h3>
    <Label class="space-y-2">
      <span>Name</span>
      <Input type="text" name="from_name" placeholder="Juan Dela Cruz" bind:value={clearName} required />
    </Label>
    <!-- <Label class="space-y-2">
      <span>Email</span>
      <Input type="email" name="from_email" placeholder="name@domain.com" bind:value={clearEmail} required/>
    </Label> -->
	<Label class="space-y-2">
      <span>Your message</span>
	  <Textarea id="textarea-id" placeholder="Your message" rows={4} name="message" class="w-full" bind:value={clearMessage} required/>
    </Label>
	
    <Button type="submit" value="Send" class="w-full bg-bgBlue border border-[#ffeb3b] hover:bg-[#ffeb3b] hover:text-[#313131]">Send message</Button>

  </form>
	</Card>
</div>
<style lang="postcss">
	.cheatline {
		background-color: #ffeb3b;
		color: #313131;
	}
	:global(html) {
		background-color: theme(colors.bgBlue);
		color: #dddddd;
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
