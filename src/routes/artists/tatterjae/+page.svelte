<script lang="ts">
	import '../../../app.postcss';
	import { page } from '$app/stores';
    import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;

	import jae from "$lib/artists/tatterjae.png?enhanced";
	import jaeMobile from "$lib/artists/mobile_tatterjae.png?enhanced";

	import jae1 from "$lib/artists/jae/jae1.png?enhanced";
	import jae2 from "$lib/artists/jae/jae2.png?enhanced";
	import jae3 from "$lib/artists/jae/jae3.png?enhanced";
	import jae4 from "$lib/artists/jae/jae4.png?enhanced";
	import jae5 from "$lib/artists/jae/jae5.png?enhanced";
	import jae6 from "$lib/artists/jae/jae6.png?enhanced";
	import jae7 from "$lib/artists/jae/jae7.png?enhanced";
	import jae8 from "$lib/artists/jae/jae8.png?enhanced";
	import jae9 from "$lib/artists/jae/jae9.png?enhanced";
	import jae10 from "$lib/artists/jae/jae10.png?enhanced";

	const jaeImages:{[key:string]:string} = {jae1, jae2, jae3, jae4, jae5, jae6, jae7, jae8, jae9, jae10};

	let imageSelection = 1;
	//Standardize image ratio of 1 in height to 0.8 in width, variable alts
	//Percentage is based on the element's container, viewport lengths are always based on the entire screen

	function increment()
	{
		imageSelection = imageSelection + 1;
		if(imageSelection > 10)
			imageSelection = 1;
	}
	function decrement()
	{
		imageSelection = imageSelection - 1;
		if(imageSelection < 1)
			imageSelection = 10;
	}
</script>

<svelte:head>
	<title>
		@tatterjae Portfolio
	</title>
	<meta name="description" content="Take a look at @tatterjae's tattoo portfolio here.">
</svelte:head>

<enhanced:img class="absolute flex flex-col lg:hidden top-[20.5vw] w-[100%] h-auto -z-10 select-none" src={jaeMobile} alt="instagram screen"/>
<enhanced:img class="absolute hidden lg:flex lg:w-[118vh] lg:h-[100vh] lg:left-[30vw] lg:max-h-none lg:max-w-none -z-10 select-none" src={jae} alt="instagram screen"/>

<div class="flex lg:hidden">
	<a class="mx-auto" href="/artists/domthekidtattoos"><Icon name="arrow-left-outline" class="h-[20vw] w-auto text-white" /></a>
	<a class="mx-auto" href="/artists/gomezink"><Icon name="arrow-right-outline" class="h-[20vw] w-auto text-white" /></a>
</div>

<div class="relative flex flex-col w-[100%] h-[138vw] max-h-none max-w-none lg:flex-row lg:w-[118vh] lg:h-[100vh] lg:left-[30vw] select-none">

	<a class="relative h-auto w-[54.1%] top-[27%] left-[22.7%] lg:h-[42%] lg:w-auto lg:left-[42.3%] lg:top-[27.7%]" href="https://www.instagram.com/tatterjae" target="_blank"><enhanced:img class="relative h-[100%] w-[100%] select-none" src={jaeImages[`jae${imageSelection}`]} alt="slideshow of tattoos"></a>

	<Icon name="arrow-left-outline" on:click={() => decrement()} class="relative max-h-none w-[9%] h-auto top-[41.5%] left-[25.4%] lg:top-[85.2%] lg:left-[10.8%] lg:h-[5%] lg:w-auto text-orange-600" />
	<Icon name="arrow-right-outline" on:click={() => increment()} class="relative max-w-none w-[9%] h-auto top-[36.4%] left-[65%] lg:top-[85.2%] lg:left-[30.5%] lg:h-[5%] lg:w-auto text-orange-600" />

	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[17.8%] left-[23%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:right-[0.3%] lg:left-[0%] {imageSelection == 1 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[16.4%] left-[28.7%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[1.5%] {imageSelection == 2 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[15%] left-[34.4%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[3.3%] {imageSelection == 3 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[13.6%] left-[40.1%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[5.1%] {imageSelection == 4 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[12.2%] left-[45.8%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[6.9%] {imageSelection == 5 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[10.8%] left-[51.5%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[8.7%] {imageSelection == 6 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[9.4%] left-[57.2%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[10.5%] {imageSelection == 7 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[8%] left-[62.9%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[12.3%] {imageSelection == 8 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[6.6%] left-[68.6%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[14.1%] {imageSelection == 9 ? "bg-black" : "bg-white"}"></div>
	<div class="relative -z-10 rounded-[50%] w-[2%] h-[1.4%] top-[5.2%] left-[74.3%] lg:w-[1.5%] lg:h-[1.5%] lg:top-[71.3%] lg:left-[15.9%] {imageSelection == 10 ? "bg-black" : "bg-white"}"></div>

	<a class="relative lg:top-[40%] lg:right-[77%] lg:w-[20%] lg:h-[17%]" href="/artists/domthekidtattoos"><Icon name="arrow-left-outline" class="relative hidden lg:flex lg:w-[100%] lg:h-[100%] text-white" /></a>
	<a class="relative lg:top-[40%] lg:left-[21%] lg:w-[20%] lg:h-[17%]" href="/artists/gomezink"><Icon name="arrow-right-outline" class="relative hidden lg:flex lg:w-[100%] lg:h-[100%] text-white" /></a>
</div>
