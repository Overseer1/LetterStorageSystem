<script>
	import MMK from '$lib/assets/ITCS/MK.jpg?url';
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
			if (hasItem && valueCheck == 'CS-15') {
			} else {
				goto(base + '/');
			}
		});
	}
</script>
<title>CS/CS-15</title>
<div class="text-center m-5">Welcome, Marson, M. K.</div>
<div class="cheatline text-center">Letter finished: June 17, 2024 | Letter written: June 17, 2024</div>
<header class="overflow-hidden mb-5 flex justify-center">
	<img src={MMK} alt="N/A" class="object-cover mt-10 h-[400px] w-[250px] rounded-lg" />
</header>
<article class="m-10 mb-3">
	Hai Marielle, so ano no, bakit kita ginagawan ng letter eh inaaway mo q palagi. De ano, thank u sa mga memories and bondings
	natin. Tsaka sa mga katarantaduhan since last school year. Ewan ko kung kanino mo nakuha yung ugali na yan pero oks lang, gago din kami eh.
	Update about sa life ko kahit alam mo na,
	wala ng gusto na babae (for now), inaatupag ang kalusugan ko dahil lumalala na ulit (alam mo naman na kung bakit), 
	and naghahanap na trabaho. Yes nagpupuyat pa din pero di na masyado (well, pinagpuyatan ko tong pag draft ng letters).
</article>
<article class="m-10 mb-3">
	So yun nga, grabe pinagsamahan natin ah, lalo na yung nagpakitang gilas pa tayo nung intrams. Nahimatay ba naman tayo eh,
	tas nadamay pa natin si Ashley. Well, at least okay na tayong tatlo. Thankful ako kase tinulungan mo pa din ako kahit pagod ka na. 
	I owe you for that. Tsaka alam ko na sinabi ko na sayo to before, pero sasabihin ko ulit.
	Doon ko narealize kung gaano ko sila kaclose, kung gaano ko kayo kaclose, at kung anong klaseng pag aalaga ang binigay 
	niyo sa akin that day. Dahil doon, magiging reason ko yon if ever na magisip ako na tapusin ang life ko. Hindi naman na mangyayari yon ever again. Thank you talaga.
	Tsaka eto pa, buti ikaw yung co-photographer ko minsan. Enthusiastic ka kase pag may hawak ka na camera eh. Baka nga ikaw na maging photographer ng school eh
	(kung want mo lang). Tsaka ang lupit mo din manggisa ah. Konting gisa pa, maaamoy ko na yung chopsuey eh. Baka nga masunog mo pa.
</article>
<article class="m-10 mb-3">
	I'm so thankful na nakilala kita, mamimiss ko talaga yung memories and bondings natin and
	Ang ganda ng pinagsamahan natin since last school year (mga random photoshoots, tamang asaran, tamang chismisan). 
	So yun nga beh, thank you again sa mga memories, kakulitan, and bondings natin! Mahal na mahal kita. God bless u, 
	ingat ka palagi, see u when I see u, and thank u ulit! To more memories with u!!!
</article>
<footer class="m-10 mr-18 text-end">
	From your school twin brother, co-photographer, and close friend, <br />
	Hanz
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
