<script>
// @ts-nocheck

	import CKC from '$lib/assets/TM/KC.jpg?url';
	import CKC1 from '$lib/assets/TM/KC1.jpg?url';
	import CKC2 from '$lib/assets/TM/KC2.jpg?url';
	import Modal from '../../components/LetterModal.svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	import emailjs from '@emailjs/browser';
	import { Card, Button, Toggle } from 'flowbite-svelte';
	let showModal = false;
	let letterContent = '';
  	let vCard = false;
	function letterShow(contentSelect){
		letterContent = contentSelect;
		showModal = true;
	}
	  const developerSide = () =>
	  {
		if (DevPass == import.meta.env.VITE_DevPass)
	  	{
			DevOpt = true
			alert('Welcome developer. Please turn off your screen sharing stream/s before proceeding.')
	  	}
		else
		{
			alert('Wrong password.')
		}
	  }
	  const LogOut = () =>
	  {
			DevAcc = false
			DevPass = false
			DevOpt = false
			alert("Thank you.");
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
			if (hasItem && valueCheck == import.meta.env.VITE_SiteKey) {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>Developer's testbench</title>
<div class="text-center m-5">Welcome, Developer.</div>
<div class="cheatline text-center mb-5">‎</div>
<hr />
<header class="overflow-hidden flex justify-center">
	<p class="text-xl m-5">
		Please select the letter you want to read.
	</p>
</header>

<!-- start of Letter UI reconstruction -->
<div class="flex justify-center max-sm:block">
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC} reverse={vCard} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Letter type</h5>
		  <p class="mb-3 font-normal leading-tight">Letter summarization.</p>
		  <Button class="bg-bgPurp hover:bg-[#6d28d9]" on:click={()=>(letterShow('Graduation'))}>
			Read more
		  </Button>
		</Card>
		<!-- <Toggle bind:checked={vCard} class="italic dark:text-gray-500">Reverse</Toggle> -->
	</div>

	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC2} reverse={vCard} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Letter type</h5>
		  <p class="mb-3 font-normal leading-tight">Letter summarization.</p>
		  <Button class="bg-bgPurp hover:bg-[#6d28d9]" on:click={()=>(letterShow('Birthday'))}>
			Read more
		  </Button>
		</Card>
		<!-- <Toggle bind:checked={vCard} class="italic dark:text-gray-500">Reverse</Toggle> -->
	</div>
	
	<div class=" overflow-hidden mb-5 flex justify-center mx-5">
		<Card img={CKC1} reverse={vCard} class="bg-current text-[#f5f3f3]">
		  <h5 class="mb-2 text-2xl font-bold tracking-tight ">Letter type</h5>
		  <p class="mb-3 font-normal leading-tight">Letter summarization.</p>
		  <Button class="bg-bgPurp hover:bg-[#6d28d9]" on:click={()=>(letterShow('Gratitude'))}>
			Read more
		  </Button>
		</Card>
		<!-- <Toggle bind:checked={vCard} class="italic dark:text-gray-500">Reverse</Toggle> -->
	</div>
	{#if letterContent === 'Graduation'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Letter type</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: | Letter written: </p>
		<div class="overflow-y-auto">
			<!-- //* you may add carousel or images in between -->
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
				Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
				Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
				<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
					Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
					Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
					<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
						Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
						Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
						<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
							Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
							Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>

							<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
								Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
								Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
								<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
									Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
									Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
									<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
										Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
										Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
										<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
											Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
											Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
											<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
												Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
												Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
												<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
													Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
													Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>


													<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>

		</div>
	</Modal>
	{:else if letterContent === 'Birthday'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Letter type</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: | Letter written: </p>
		<div class="overflow-y-auto">
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
			<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
			Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
			Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
		</div>
	</Modal>
	{:else if letterContent === 'Gratitude'}
	<Modal bind:showModal>
		<h2 slot="letterType" class="text-white text-xl cheatline text-center">Gratitude letter</h2>
		<p slot="dateOfLetter" class="text-white text-lg text-center border-b-[1px] px-5 py-2.5">Letter finished: | Letter written: </p>
		<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
		Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
		Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
		<p class="text-white text-base text-center mt-2">Cillum enim cupidatat labore culpa sint. Nostrud nostrud iruredeserunt ut pariatur. Quis mollit Lorem ex fugiat laborum mollitipsum minim Lorem pariatur occaecat exercitation. 
		Et suntreprehenderit minim ullamco elit culpa duis enim anim utincididunt. Voluptate excepteur ipsum officia cillum sint laborumtempor sint adipisicing ullamco cupidatat veniam ullamco deserunt.
		Ipsum nisi veniam Lorem magna do nisi mollit amet. Excepteur occaecat Lorem qui pariatur ea labore deserunt proident enim.</p>
	</Modal>
	{/if}
</div>
<!-- end of Letter UI reconstruction -->
 
<hr />
    
<div class="text-center mt-5">If you want, you may leave a message to the developer. <br/> You may change your name in the text box below.</div>

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
	.inputColor {
		color: #313131;
	}
	:global(html) {
		background-color: theme(colors.bgPurp);
		color: #dddddd;
	}
	@media screen and (max-width: 700px) {
		img {
			width: 77%;
		}
		.buttonChange
		{margin-right: 12px;}
		/* partial implementation only */
		/* header
		{
			display: block;
			height: auto;
			width: auto;
			margin-left:120px;
		} */
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
