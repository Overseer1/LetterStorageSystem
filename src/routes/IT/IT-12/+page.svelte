<script>
    // @ts-nocheck
        import MP from '$lib/assets/ITCS/MP.jpg?url';
        import { goto } from '$app/navigation';
        import { base } from '$app/paths';
        import { onMount } from 'svelte';
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
			if (hasItem && valueCheck == import.meta.env.VITE_IT_12_T) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
    <title>IT-2024-12</title>
    <div class="text-center m-5">Welcome, Paltingca, Ma. M.</div>
    <div class="cheatline text-center">Message finished: July 04, 2024</div>
    <header class="overflow-hidden mb-5 flex justify-center">
        <img src={MP} alt="N/A" class="object-cover mt-10 h-[260px] w-[450px] rounded-lg" />
    </header>
    <article class="m-10 mb-3">
        Hai Cedes, Thank you sa mga memories and what not since A.Y. 2022-2023. Alam mo naman na current mental situation ko ngayon so eto na lang update q sayo, 
        wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit, and naghahanap na trabaho. Nahimatay ako nung May 30 kung hindi mo alam. Pero okay naman na ako.
    </article>
    <article class="m-10 mb-3">
        Maikli lang naman to so ganto, thank you sa mga times na ginawa mo akong personal photographer mo. Masaya din naman yon kahit paano. Tsaka also, thank you din sa mga bondings and sa times
        na naging rant person kita and lastly, thank you sa time na kinamusta mo ako nung hindi ako okay. Ayoko sabihin naman kung ano yung nag push sa akin kung bakit, pero inside my head lang naman
        yon eh. Thank you talaga. Thankful ako na nakilala kita Cedes, I didn't know din na mag ca-care ka sa akin sa times na hindi ako okay. So yun nga, thank you sa 2 years worth of memories, bondings, and being my motivation and inspiration
        for 4 months (3Y2 yon). Love u beh, God bless u and ingat ka palagi. Congrats sa atin at nakagraduate na tayo! Goodluck sa magiging future mo and to more memories with u!!!
    </article>
    <footer class="m-10 mr-18 text-end">
        From your photographer and friend, <br />
        Hanzyboy<br />
    </footer>
    <hr />
    
    <div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
    <form on:submit|preventDefault={sendEmail}>
        <div class="flex justify-center">
            <input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Cedes" required>
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
    