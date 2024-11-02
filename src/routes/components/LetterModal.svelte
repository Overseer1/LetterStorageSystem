<script>
	/**
	 * @type {boolean}
	 */
	 export let showModal; // boolean
	/**
	 * @type {HTMLDialogElement}
	 */
	let dialog; // HTMLDialogElement

	$: if (dialog && showModal) dialog.showModal();
</script>

<!-- svelte-ignore a11y-click-events-have-key-events a11y-no-noninteractive-element-interactions -->
<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
<dialog
	bind:this={dialog}
	on:close={() => (showModal = false)}
	on:click|self={() => dialog.close()}
	class="bg-transparent backdrop-blur-3xl snap-start"
>
	<!-- //TODO have the bg color dynamic for the whole modal. -->
	<!-- svelte-ignore a11y-no-static-element-interactions -->
	<div on:click|stopPropagation class="snap-start" tabindex="-1">
		<slot name="letterType" />
        <slot name="dateOfLetter" />
		<slot />
		<!-- svelte-ignore a11y-autofocus -->
		<button autofocus on:click={() => dialog.close()} class="text-white inline-flex w-full justify-center text-lg px-5 py-2.5 inset-x-0 bottom-0 text-center border-t-[1px] mt-2">Close</button>
	</div>
</dialog>

<style>
	dialog {
		max-width: 800px;
		max-height: 90vh;
		border-radius: 0.5em;
		border: none;
		padding: 0;
	}
	@media screen and (max-width: 700px){
		dialog{
			margin-right: 20px;
			margin-left: 20px;
			height: 600px;
		}
	}
	dialog::backdrop {
		background: rgba(0, 0, 0, 0.3);
	}
	dialog > div {
		padding: 1em;
	}
	dialog[open] {
		animation: zoom 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
	}
	@keyframes zoom {
		from {
			transform: scale(0.95);
		}
		to {
			transform: scale(1);
		}
	}
	dialog[open]::backdrop {
		animation: fade 0.2s ease-out;
	}
	@keyframes fade {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}
	button {
		display: block;
	}
</style>