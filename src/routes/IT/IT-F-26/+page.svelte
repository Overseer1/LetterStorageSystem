<script>
    // @ts-nocheck
    
        import FC from '$lib/assets/ITCS/C.jpg?url';
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
                if (hasItem && valueCheck == 'IT-F-26') {
                } else {
                    goto(base + '/');
                }
            });
        }
    </script>
    <title>IT/IT-F-26</title>
    <div class="text-center m-5">Welcome, Mr. Fajardo, C.</div>
    <div class="cheatline text-center">Message finished: October 3, 2024</div>
    <header class="overflow-hidden mb-5 flex justify-center">
        <img src={FC} alt="N/A" class="object-cover mt-10 h-[250px] w-[450px] rounded-lg" />
    </header>
    <article class="m-10 mb-3">
        Wasap boi, Happy teacher's day! So ayun nga no, eto lang regalo ko sayo unless makahanap pa ako nang madagdag dito, wag ka na magreklamo HSHSHAHAAHHAS tsaka wala naman ako naririnig na reklamo about sa teaching mo
        or sayo mismo so safe ka naman
        HDSHASHAHAHA basta boi galingan mo sa pagtuturo, total naman eh goods na goods ka daw mag turo tsaka masaya ka din naman sa trabaho mo so ayon. 
        Enjoy your day and happy teacher's day ulit!!!
    </article>
    <footer class="m-10 mr-18 text-end">
        From your helpdesk, photographer, and friend, <br />
        Hanz
    </footer>
    <hr />
        
    <div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
    <form on:submit|preventDefault={sendEmail}>
        <div class="flex justify-center">
            <input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Ceejay" required>
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
    