<script>
    // @ts-nocheck

        import J from '$lib/assets/ITCS/JB.jpg?url';
        import J2 from '$lib/assets/ITCS/JB2.jpg?url';
        import J3 from '$lib/assets/ITCS/JB3.jpg?url';
        import J4 from '$lib/assets/ITCS/JB4.jpg?url';
        import J5 from '$lib/assets/ITCS/JB5.jpg?url';
        import Modal from '../../components/LetterModal.svelte';
        import { Card, Button, Toggle, Spinner } from 'flowbite-svelte';
        import { goto } from '$app/navigation';
        import { onMount } from 'svelte';
        import { base } from '$app/paths';
        import Icon from '@iconify/svelte';
        import emailjs from '@emailjs/browser';
        let showModal = false;
	    let letterContent = '';
	    function letterShow(contentSelect) {
		letterContent = contentSelect;
		showModal = true;
	    }
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
                if (hasItem && valueCheck == import.meta.env.VITE_IT_20_T) {
                } else {
                    goto(base + '/');
                }
            });
        }
    </script>
    <title>Hallo ate Judayyyy</title>
    <div class="text-center m-5">Welcome, Ms. Belda, J.</div>
    <div class="cheatline text-center">Page updated: February 27, 2025</div>
    <header class="overflow-hidden mb-5 flex justify-center">
        <img src={J} alt="N/A" class="object-cover mt-10 h-[250px] w-[450px] rounded-lg" />
    </header>
    <hr />
    <header class="overflow-hidden flex justify-center cheatline my-5">
        <p class="text-lg">Please select the letter that you want to read.</p>
    </header>
    <div class="flex justify-center max-sm:block">
        <div class="overflow-hidden mb-5 flex justify-center mx-5">
            <Card img={J2} reverse={false} class="bg-current text-[#f5f3f3]">
                <h5 class="mb-2 text-2xl font-bold tracking-tight">Gratitude letter</h5>
                <p class="mb-3 font-normal leading-tight">Desc here.</p>
                <Button
                    class="bg-bgBlue border border-[#ffeb3b] hover:bg-[#ffeb3b] hover:text-[#313131]"
                    on:click={() => letterShow('Gratitude')}
                >
                    Open letter
                </Button>
            </Card>
        </div>
        <div class="overflow-hidden mb-5 flex justify-center mx-5">
            <Card img={J5} reverse={false} class="bg-current text-[#f5f3f3]">
                <h5 class="mb-2 text-2xl font-bold tracking-tight">Birthday letter</h5>
                <p class="mb-3 font-normal leading-tight">Desc here.</p>
                <Button
                    class="bg-bgBlue border border-[#ffeb3b] hover:bg-[#ffeb3b] hover:text-[#313131]"
                    on:click={() => letterShow('Birthday')}
                >
                    Open letter
                </Button>
            </Card>
        </div>
        {#if letterContent === 'Gratitude'}
	    <Modal bind:showModal>
		<h2 slot="letterType" class="text-[#313131] text-xl cheatline text-center">Birthday letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: N/A </p>
		<div class="text-[#f5f3f3]">
			<article class="m-5">
				dfsfds
			</article>
			<article class="m-5">
				dfsfds
			</article>
			<article class="m-5">
				dfsfds
			</article>
			<article class="m-5">
				dfsfds
			</article>
			<footer class="m-5 text-end">
                From your photographer and bff, <br />
                Hanz
			</footer>
		</div>
	</Modal>
        {:else if letterContent === 'Birthday'}
	    <Modal bind:showModal>
		<h2 slot="letterType" class="text-[#313131] text-xl cheatline text-center">Birthday letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: N/A</p>
		<div class="text-[#f5f3f3]">
			<article class="m-5">
				Hai ate Judayyyy, HAPPY BIRTHDAY SAYOOOOO!!! sori ah late na late na to
			</article>
			<article class="m-5">
				dfsfds*
			</article>
			<article class="m-5">
				dfsfds*
			</article>
			<article class="m-5">
                dfsfds*
			</article>
			    <footer class="m-5 text-end">
				    From your photographer and bff, <br />
                    Hanz
			    </footer>
		    </div>
	    </Modal>
        {/if}
    </div>
    <hr />
    <div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>
    <form on:submit|preventDefault={sendEmail}>
        <div class="flex justify-center">
            <input type="text" placeholder="Name" name="from_name" class=" border rounded-lg text-black m-4 p-1 inputColor" value="Ate Juday" required>
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
    