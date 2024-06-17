<script>
	import CKC from '$lib/assets/TM/KC.jpg?url';
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
			if (hasItem && valueCheck == 'TM-KC') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>TM/TM-KC</title>
<div class="text-center m-5">Welcome, Cabrera, K. C.</div>
<div class="cheatline text-center">Letter finished: June 10, 2024 | Letter written: June 11, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={CKC} alt="N/A" class="object-cover mt-10 h-[250px] w-[450px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	Hai Kat Kattt, mag thank u lang ako sa mga memories na nagawa natin together and sa kung saan pa.
	Alam mo, mamimiss kita ng sobra sobra. Kase araw araw ako pumapasok tas araw araw din kita
	nakikita. Tapos kung want mo magphotoshoot, ginagawa naman natin. Hindi lang dahil sa crush kita
	and what not, dahil sa malapit kita na kaibigan and syempre, memories mo na din yon sa school pag
	nakagraduate ka na. Thank you dahil sa naging inspiration and motivation kita! Alam mo naman na kung bakit kita nagustuhan eh.
  Pero sabihin ko ulit, Maganda ka, mag ka-vibes tayo, same tayo ng music taste, hindi ka naninigarilyo, and syempre mabait ka.
</article>
<article class="m-10">
	Sana talaga maging Cum Laude graduate ka. I'm rooting for you beh. Palagi mo tandaan na nandito
	ako para sayo, kahit anong mangyari. Nakakatuwa din na naging close friend kita. Ang saya kase ng
	usapan natin palagi eh, tamang VMs, purong kapakshitan (AMEX PLATINUM, GALVANIZED SQUARE STEEL), tas sa mga
	nanggugulo sayo. Ang saya mo talaga kausap Kat Kat. To be honest beh, ikaw yung isa sa mga tao na
	ginawang bearable ang internship ko dahil sa kayo yung nilalapitan ko about doon. Rant dito about
	sa pinapagawa, rant doon sa kasabay ko, you get the point naman. Thank you, kase available ka
	kausapin if mag rant ako or chismis or what not. Sana ganon ka din in the future, pero if
	sasabihin mo na busy ka, hindi naman kita pipilitin. Basta mailahad ko lang yung want ko sabihin,
	masaya na ako. As long na nabasa mo. Tsaka next time, 'wag na kayong mag-away na magkapatid nang basta-basta.
  Nahirapan ako na ikalma kayong pareho noon eh. Pero if ever na mangyari ulit yon, kahit ako ulit ang gawin niyong mediator.
  Wala ako problem doon. Basta na ako lang ang mediator niyo.
</article>
<article class="m-10">
  Sorry sa mga times na nagiging needy ako sa replies mo kahit alam ko na busy ka ng sobra and sa times na
  hindi kita natutulungan sa schoolworks or sa pagbigay ng advice during rants mo kase nablangko utak ko. 
  Tsaka pala, if need mo ng kausap about sa life or schoolworks
	or kung ano man yan, I'm here for you. Alam mo yan beh. Kahit na kausap ko kapatid mo about sa rants niya, kinakausap pa din kita about sa rants mo.
	Tsaka yung sa photoshoots natin, ang saya din non. Why? kase ikaw yung una ko naging personal
	model/subject sa mga photoshoots. Tsaka ang dami na din natin na photoshoots ah (3 or 5 na ata).
	Hindi mo pa naman nasasakop ng pictures mo yung SD card kaya safe ka pa. If want mo mag photoshoot, sabihan mo lang ako, alam ko naman na want mo din eh.
  Sasabihan naman kita kung free ako. Tsaka mag photoshoot/gala tayo minsan beh, pwedeng tayo lang dalawa or kasama si Asli, si Fem, or kung sino pa na want mo isama.
  Tsaka eto, 'wag mo isipin problems mo sa life as much as possible. Mag focus ka sa studies mo pa. Tignan mo ilang semesters
	na lang, tapos ka na. May latin honors pa. Sana talaga Kat na makatapos ka with latin honors. Like
	I said kanina, I'm rooting for you and I'll support you every step of the way.
</article>
<article class="m-10">
	I'm so thankful na nakilala kita Kat Kat, actually thankful ako sa inyong magkapatid. Ang ganda ng pinagsamahan natin kahit nung January lang
	tayo nag start na mag usap. So yun nga beh, thank you again sa mga memories, bondings, and for
	being my inspiration and motivation for this last semester. Mahal na mahal kita Kat. Pareho ko kayong mahal magkapatid. God bless u
	and ingat ka palagi. To more memories with u!!!
</article>
<footer class="m-10 mr-18 text-end">
	From your personal photographer and close friend, <br />
	Hanz
</footer>
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
	}
</style>
