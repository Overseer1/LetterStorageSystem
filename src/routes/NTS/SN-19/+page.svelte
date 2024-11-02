<script>
// @ts-nocheck

	import TA from '$lib/assets/NTS/SN-A.jpg?url';
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
			if (hasItem && valueCheck == import.meta.env.VITE_SN_19_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>NTS/SN-19</title>
<div class="text-center m-5">Welcome, Ms. Tabigne, A.</div>
<div class="cheatline text-center">Letter finished: June 12, 2024 | Letter written: June 13, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={TA} alt="N/A" class="object-cover mt-10 h-[250px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	Hai Ma'am, thank u sa mga memories, medical advice, and sa pag aalaga sa akin! Kahit part ng trabaho mo is mag
	care ng patients katulad ko, thankful pa din aq sayo ma'am. So update sa life q ma'am, yes nakakainom na ng gamot for thyroid,
	naaalagaan ko naman sarili ko (yes nag eexercise naman ako thru dancing), and syempre, nagpapahinga para makarecover both physically 
	and mentally. Tsaka medyo nagpupuyat pa din (sori).
</article>
<article class="m-10 mb-3">
	About sa mental health, kagaya ng sinabi q kay Ma'am Quinnah sa letter niya, 
	Rarely na nakakaisip ng no good pero no, I won't do it na kase na open na eyes ko sa mangyayari. Kaya safe naman ako dyan ma'am. Syempre thankful din aq sa mga times na nagkakaroon ng random photoshoots and kamustahan, Kase madalang din ako makakuha ng ganong tanong.
	About don sa photoshoots, may Thursday and Friday naman kaya keri pa. Madami pa space sa aking SD card kaya ayun. About naman sa medical advices,
	yes sinusunod ko naman, may times lang na hindi kase walang money na pambili and may times din na di ko nasusunod yung tamang pagkain 
	(e.g. kumakain ng high cholesterol and high uric acid na foods, hindi kumakain sa tamang oras) pero, I'm doing my best na ayusin yung habits na iyon. About naman sa nangyari nung May 30,
	sobrang thankful aq sayo ma'am kase inalagaan mo ako, si Marielle, at si Ashley. Hindi ko makakalimutan yon ma'am. And yes, natrauma ako noon kase nakita ko
	na yung dalawa ko na kaibigan na nahimatay pero, at least okay na sila. Eye opener din yung 1 week break q sa school. Ang dami ko na realize sa life. Kaya thank you dahil sabi niyo din na magpahinga aq for 1 week.
</article>
<article class="m-10 mb-3">
	Mamimiss q yung photoshoots, usapan, and paghihingi ng kung anong pagkain mo ma'am. Tsaka pala, thank you sa mga random na libre mo na foods. 
	Babawi aq sayo ma'am. Salamat sa 2 semesters na kulitan, pag alaga, at bonding ma'am! Kakamustahin kita every now and then.
	Mamimiss kita ma'am! Love u ma'am! Don't worry ma'am, aalagaan ko sarili ko. God bless u, see u when I see u and thank u ulit!!! 
</article>
<footer class="m-10 mr-18 text-end">
	From your photographer, patient, and friend, <br />
	Hanzyboy
</footer>

<hr />
    
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
<form on:submit|preventDefault={sendEmail}>
	<div class="flex justify-center">
		<input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Ma'am Alelie" required>
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
		background-color: #8f011b;
		color: #dddddd;
	}
	:global(html) {
		background-color: theme(colors.bgMaroon);
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
