<script>
// @ts-nocheck

	import MJ from '$lib/assets/TM/J.jpg?url';
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
	$: {
		let hasItem;
		let valueCheck;
		onMount(async () => {
			hasItem = localStorage.getItem('letterKey') !== null;
			valueCheck = localStorage.getItem('letterKey');
			// Conditional logic based on hasItem
			if (hasItem && valueCheck == 'TM-10') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>TM/TM-10</title>
<div class="text-center m-5">Welcome, Margate, J.</div>
<div class="cheatline text-center">Letter finished: June 13, 2024 | Letter written: June 14, 2024 | Letter updated: July 04, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={MJ} alt="N/A" class="object-cover mt-10 h-[250px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	Hai Jovy/Anakis, thank u for the memories and bonding sa life and sa school. Mamimiss q yon and yung mga random photoshoots natin.
	Oo, kaya pa ng camera ko pagmumukha mo kase sabi ko. Himala nga na kaya pa eh.
	Alam mo naman na current status ko sa life, wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit, 
	and naghahanap na trabaho. Yes nagpupuyat pa din pero di na masyado (well, pinagpuyatan ko tong pag draft ng letters).
</article>
<article class="m-10 mb-3">
	So yun nga no, thankful ako na kilala kita. Why? kase ikaw ang reason kung paano ko nakilala ang magkapatid at si Fem. Ikaw ang reason kung bakit
	nabuo ulit yung 2nd circle ko. Kayo yung pumalit sa mga former members noon and I'm proud. Isipin mo yon, ikaw yung naging reason sa reformation
	ng 2nd circle ko. Ang lupit no? Ikaw kase eh. Ang uniqueness lang ng 2nd circle is majority ay babae. Parang naging babaero ako doon ah, pero meh,
	at least kaibigan ko kayo and you all know it naman. Speaking of that, ang uniqueness sayo is yung bigla mo akong ginawang tatay. Ewan q kung bakit mo naisip 
	yon pero sige, you do you girl. Tsaka eto pala, thank you at tumulong ka sa hide and seek natin nung nahimatay ako. Inalalayan mo pa nga ako eh, kaso na kay
	Marielle yung bigat HSHAHA tas nag domino effect pa. Alam ko na say ko na to sayo pero here oh, doon ko narealize kung gaano ko sila kaclose, kung gaano ko kayo kaclose, at kung anong klaseng pag aalaga ang binigay 
	niyo sa akin that day. Dahil doon, magiging reason ko yon if ever na magisip ako na tapusin ang life ko. Hindi naman na mangyayari yon ever again. Malaki ang utang na loob ko sa inyo. Thank you so much.
</article>
<article class="m-10 mb-3">
	I'm so thankful na nakilala kita Jovy, mamimiss ko talaga yung memories and bondings natin and thankful talaga ako sa reformation ng 2nd circle dahil sayo. Ang ganda ng pinagsamahan natin since last sem
	(mga random photoshoots, tamang pag comfort sayo pag malungkot ka, inalalay mo aq nung May 30, tamang asaran, tamang chismisan). 
	So yun nga anakis, thank you again sa mga memories, kakulitan, and bondings natin! Mahal na mahal kita anakis. Thank you for being the foundation ng 2nd circle! God bless u, 
	ingat ka palagi, see u when I see u, and thank u ulit! To more memories with u!!!
</article>
<footer class="m-10 mr-18 text-end">
	From your school father, photographer, and close friend, <br />
	Hanz
</footer>
<article class="m-10 mb-3">
	P.S. Oo alam ko na aalis ka na soon kaya nilagay ko na dito yung leave a message. Ikaw na bahala kung gagamitin mo or not, pero please keep in touch ha? Yun lang naman, ingat ka
	palagi and love u so mats!
</article>

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
