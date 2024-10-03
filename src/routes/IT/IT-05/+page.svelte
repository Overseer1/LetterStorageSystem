<script>
// @ts-nocheck

	import EKJ from '$lib/assets/ITCS/KJ.jpg?url';
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
			if (hasItem && valueCheck == 'IT-05') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>IT/IT-05</title>
<div class="text-center m-5">Welcome, Estipona, K.</div>
<div class="cheatline text-center">Letter finished: June 17, 2024 | Letter written: June 17, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={EKJ} alt="N/A" class="object-cover mt-10 h-[260px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	Hai Tin, thank u sa mga memories and bondings natin. Mamimiss q yung random pitch sales mo sa akin tsaka
	yung minsanan na rant q sayo. Tas kung minsan, nag bibigay ka advice sa akin dahil sa mga pinaggagawa ko before
	(attempted na ano sa life). Dahil dyan, bibigyan kita update sa life, wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit (alam mo naman na kung bakit), 
	and naghahanap na trabaho.
</article>
<article class="m-10 mb-3">
	Yes nagpupuyat pa din pero di na masyado (well, pinagpuyatan ko tong pag draft ng letters) and rarely na nakakaisip ng no good pero no, I won't do it na kase na open na eyes ko sa mangyayari.
	Thank u sa mga advices mo and yun nga, sa mga pitch sales mo. Yes, sinusunod ko naman advice mo (from time to time) and yes, natutuwa ako sa mga pitch sales mo minsan.
	Kung iniisip mo kung ano yung pitch sales na tinutukoy ko, well yun yung times na sinasabi mo na bumili ako ng pagkain and/or drinks sayo (e.g. Mango Tapioca, Graham Balls).
	Galing mo din eh, nacoconvince mo q na bumili kaya ayun, may maneh ka na at may food aq. Good trade naman yon. Tsaka eto pa, mamimiss q random photoshoots natin, kagaya ng nandito sa page ngayon at yung
	1x1 mo para sa CV mo sa capstone docu (ata nakalimutan q na yon). Syempre thankful aq na nakilala at naging close friend kita. Kagaya nga ng sinabi ko kanina, naging advisor kita kaya ayun.
</article>
<article class="m-10 mb-3">
	I'm so thankful na nakilala kita Tin, mamimiss ko talaga yung memories and bondings natin and
	ang ganda ng pinagsamahan natin since last school year (mga random photoshoots, tamang asaran, tamang chismisan). 
	So yun nga beh, thank you again sa mga memories, kakulitan, and bondings natin! Mahal na mahal kita Tin. God bless u, 
	ingat ka palagi, see u when I see u, and thank u ulit! To more memories with u!!!
</article>
<footer class="m-10 mr-18 text-end">
	From your photographer, customer, and close friend, <br />
	Hanzyboy
</footer>

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
