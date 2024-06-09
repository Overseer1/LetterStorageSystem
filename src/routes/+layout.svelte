<script>
    import "../app.css";
    import Footer from "../routes/components/Footer.svelte";
</script>
<div>
    <!-- <div class="sticky top-0 flex">
		<NavBar/>
	</div> -->
	<main class="sticky top-0">
		<slot />
	</main>
	<div class="text-xl text-white text-center fixed inset-x-0 bottom-0 p-1 bgFooter">
		<Footer />
	</div>
</div>
<style lang="postcss">
	.bgFooter {
      color: #dddddd;
    }
	:global(html) {
        background-color: theme(colors.bgBlack);
      }
</style>