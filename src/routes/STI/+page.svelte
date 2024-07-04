<script>
// @ts-nocheck

	import { goto } from '$app/navigation';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
  const sendEmail = (/** @type {{ target: string | HTMLFormElement; }} */ e) => {
    emailjs
      .sendForm(import.meta.env.VITE_EmailJS_ServiceID, import.meta.env.VITE_EmailJS_TemplateIDSTI, e.target, {
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
<div class="text-center m-5">Welcome, STIers</div>
<div class="cheatline text-center">Letter finished: July 05, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<!-- //!insert img if applicable -->
	<!-- <img src={//! insert import variable here} alt="N/A" class="object-cover mt-10 h-[260px] w-[450px] rounded-lg" /> -->
</header>
<article class="m-10 mb-3">
	Hello, STIers. Thank you for 6 years worth of memories. From Senior High School to College, ang dami ko na nakuhang lessons sa inyo. To all my teachers and former teachers, 
	thank you sa mga valuable lessons na tinuro at binigay niyo po sa akin. I'll keep those in mind. Sa mga naging kaklase ko throughout my stay sa STI, salamat din sa inyo sa mga 
	bondings and memories, Specially doon sa first and second circle ko. Alam niyo naman na yon. Sa mga napitikan ko, ayusin niyo posing niyo sa magiging next school photographer ha?
	baka masungit yon. Tsaka kung may post request pa kayo, sabihan niyo na agad ako. Sa mga natulungan ko nung naging HelpDesk ako ng mga kaklase ko at Co-IT students, salamat din sa inyo kase natutunan ko din yung ibang errors na hindi ko maayos. And finally,
	Sa mga Non-Teaching Staff, salamat sa mga tulong na binigay niyo sa akin, lalo na sa times na hindi ko na kaya. Again, Thank you STI College Sta. Maria for being your student for 6 years. I hope na 
	nakaiwan ako ng magandang legacy sa inyo. Cheers to all of you and salamat sa mga greetings niyo! God bless you and thank you!
</article>
<footer class="m-10 mr-18 text-end">
	From your student, student photographer, student IT HelpDesk, and classmate, <br />
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
