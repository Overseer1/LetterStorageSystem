<script>
// @ts-nocheck

	import RA from '$lib/assets/NTS/SL-A.jpg?url';
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
			if (hasItem && valueCheck == 'SL-24') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>NTS/SL-24</title>
<div class="text-center m-5">Welcome, Mrs. Rosal, A.</div>
<div class="cheatline text-center">Letter finished: June 13, 2024 | Letter written: June 13, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={RA} alt="N/A" class="object-cover mt-10 h-[270px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	Hai pi ma'am, thank u sa mga memories sa library and sa mga advice sa life. Tas syempre, thank you sa pagiging
	one of the second parents sa school. Ang dami ko din natutunan sayo ma'am (hindi sa pag aayos ng libro syempre).
	Alam mo naman na ma'am ang current status ko sa life, wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit, 
	and naghahanap na trabaho. Yes nagpupuyat pa din pero di na masyado (sori).
</article>
<article class="m-10 mb-3">
	So yun nga ma'am, buti na lang na nakilala kita kase yun nga, naging second parent din kita dahil sa mga advices mo sa life and sa kung saan pa.
	Tapos minsan, nagiging volunteer S.A. ako, kase kung hindi busy ang mga S.A., kumakain sila. Kaya ayun, nagiging volunteer S.A. tuloy ako. 
	Pero ok lang naman kase minsan lang naman mangyari yon. About naman sa health ko, yes oki lang ako, umiinom naman ng gamot and what not, and nag eexercise na ako
	kaso sa dancing (pwede na). Tapos pala ma'am, thank you sa inalagaan mo kaming tatlo ni Ashley at Marielle nung May 30. Grabe din kase yung pagod eh. Tapos grabe pa yung 
	ginawa nung dalawa. Si Marielle inalalay ako, si Ashley kahit pagod at puyat, tumakbo para lang kunin yung first aid kit sa clinic. Malaki ang utang na loob ko sa kanila ma'am.
	Forever grateful ako sa inyong lahat. Add ko din to ma'am, doon ko narealize kung gaano ko sila kaclose, kung gaano ko kayo kaclose, at kung anong klaseng pag aalaga ang binigay 
	niyo sa akin that day. Dahil doon ma'am, magiging reason ko yon if ever na magisip ako na tapusin ang life ko. Hindi naman na mangyayari yon ever again. Thank you talaga ma'am.
</article>
<article class="m-10 mb-3">
	Mamimiss q yung random photoshoots and advices mo ma'am. Ang dami din nangyari sa loob ng apat sem (advices about sa life and wherever, photoshoot hanggang mag sawa at mapagod
	,tamang flex ng mga kakaibang suot sa library, pagiging volunteer S.A., pag aalaga sa amin nung May 30). 
	Salamat sa 20 months or half ng aking college life na kakulitan, tulungan, and bonding ma'am! Kakamustahin kita every now and then.
	Mamimiss kita ma'am! Love u ma'am! God bless u, see u when I see u, and thank u ulit!!!
</article>
<footer class="m-10 mr-18 text-end">
	From your volunteer S.A., photographer, and friend, <br />
	Hanzyboy
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
