<script>
	import GQ from '$lib/assets/NTS/GA-Q.jpg?url';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import Icon from '@iconify/svelte';
	$: {
		let hasItem;
		let valueCheck;
		onMount(async () => {
			hasItem = localStorage.getItem('letterKey') !== null;
			valueCheck = localStorage.getItem('letterKey');
			// Conditional logic based on hasItem
			if (hasItem && valueCheck == 'GA-15') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>

<div class="text-center m-5">Welcome, Ms. Gregorio, Q.</div>
<div class="cheatline text-center">Letter finished: June 10, 2024 | Letter written: ongoing</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={GQ} alt="N/A" class="object-cover mt-10 h-[260px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	Hai Ma'am, so yun nga no, thank u sa mga memories and advices na binigay mo sa akin and sa mga libre din!
	Bigyan kita ng update ma'am, yes, alive and well aq. Nagpapahinga kase orders 'yon ng Nurse, Doctor, and syempre yourself. 
	Ginagawa ang letter and website ng puyat (sori pi). 
	Rarely na nakakaisip ng no good pero no, I won't do it na kase na open na eyes ko sa mangyayari. 
	Tsaka don't worry ma'am, nakakausap ko naman friends ko about don if ever. 
</article>
<article class="m-10">
	Thankful din aq ma'am sa mga opportunities na binigay mo sa akin, like mag picture sa events (e.g. Mental Health Week) and again nga, sa mga libreng foods hehe.
	Doon sa mga advices mo ma'am, sinusunod q naman. I'm doing my best na ayusin sarili ko both physically and mentally.
	Kaya naman to ma'am, tiwala lang. Sorry din ma'am na minsan ay hindi ko nasusunod yung advices mo kase hindi na nakakapag focus sa sarili and na-overworked pa last month dahil lang sa pics.
	Na-oorganize ko na sarili ko ma'am kaya ayun. So about sa photoshoots, yes ma'am, before ka umalis sa school magkakaroon ka photoshoot,
	sa Thursday and Friday. Madami pa naman storage yung SD card ma'am at hindi pa nag sasawa yung camera sayo ma'am. 
	Tas magreregalo aq syempre. Secret na lang kung ano yon (no hindi yung hardcopy ng letter).
</article>
<article class="m-10">
	Mamimiss q yung random photoshoots and rants mo ma'am. Ang dami din nangyari sa loob ng tatlong sem (advices about sa life, photoshoot hanggang mag sawa, kinalma aq dahil sa nangyari last May 30). 
	Salamat sa ~15 months na kakulitan, counseling, and bonding ma'am!
	Mamimiss kita ma'am! Love u ma'am! See u when I see u and thank u ulit!!!
</article>

<footer class="m-10 mr-18 text-end">
	From your photographer and friend, <br />
	Hanzyboy
</footer>
<button class="m-10 float-end border rounded-lg p-2" on:click={() => goto(base + '/')}>
	<Icon icon="ep:back" style="color: #dddddd" />
</button>

<style lang="postcss">
	.cheatline {
		background-color: #fd5da8;
		color: #eeeeee;
	}
	:global(html) {
		background-color: theme(colors.bgPink);
		color: #dddddd;
	}
	@media screen and (max-width: 600px) {
		img {
			width: 77%;
		}
	}
</style>
