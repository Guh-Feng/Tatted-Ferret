<script lang="ts">
	import '../../../app.postcss';
	import { page } from '$app/stores';
    import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;

	import carlos from '$lib/artists/gomezink.png?enhanced';
	import carlosMobile from '$lib/artists/mobile_gomezink.png?enhanced';

	import carlos1 from '$lib/artists/carlos/carlos1.png?enhanced';
	import carlos2 from '$lib/artists/carlos/carlos2.png?enhanced';
	import carlos3 from '$lib/artists/carlos/carlos3.png?enhanced';
	import carlos4 from '$lib/artists/carlos/carlos4.png?enhanced';
	import carlos5 from '$lib/artists/carlos/carlos5.png?enhanced';
	import carlos6 from '$lib/artists/carlos/carlos6.png?enhanced';
	import carlos7 from '$lib/artists/carlos/carlos7.png?enhanced';
	import carlos8 from '$lib/artists/carlos/carlos8.png?enhanced';
	import carlos9 from '$lib/artists/carlos/carlos9.png?enhanced';
	import carlos10 from '$lib/artists/carlos/carlos10.png?enhanced';

	const carlosImages:{[key:string]:string} = {carlos1, carlos2, carlos3, carlos4, carlos5, carlos6, carlos7, carlos8, carlos9, carlos10}

	let imageSelection = 1;
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
		@gomezink Portfolio
	</title>
	<meta name="description" content="Take a look at @gomezink's tattoo portfolio here.">
</svelte:head>

<enhanced:img class="absolute flex flex-col lg:hidden top-[20.5vw] w-[100%] h-auto -z-10 select-none" src={carlosMobile} alt="instagram screen"/>
<enhanced:img class="absolute hidden lg:flex lg:w-[118vh] lg:h-[100vh] lg:left-[30vw] lg:max-h-none lg:max-w-none -z-10 select-none" src={carlos} alt="instagram screen"/>

<div class="flex lg:hidden">
	<a class="mx-auto" href="/artists/tatterjae"><Icon name="arrow-left-outline" class="h-[20vw] w-auto text-white" /></a>
	<a class="mx-auto" href="/artists/domthekidtattoos"><Icon name="arrow-right-outline" class="h-[20vw] w-auto text-white" /></a>
</div>

<div class="relative flex flex-col w-[100%] h-[138vw] max-h-none max-w-none lg:flex-row lg:w-[118vh] lg:h-[100vh] lg:left-[30vw] select-none">

	<a class="relative h-auto w-[54.1%] top-[27%] left-[22.7%] lg:h-[42%] lg:w-auto lg:left-[42.3%] lg:top-[27.7%]" href="https://instagram.com/gomezink" target="_blank"><enhanced:img class="relative -z-10 h-[100%] w-[100%] select-none" src={carlosImages[`carlos${imageSelection}`]} alt="slideshow of tattoos"></a>

	<Icon name="arrow-left-outline" on:click={() => decrement()} class="relative max-h-none w-[9%] h-auto top-[41.5%] left-[25.4%] lg:top-[85.2%] lg:left-[10.8%] lg:h-[5%] lg:w-auto text-green-600" />
	<Icon name="arrow-right-outline" on:click={() => increment()} class="relative max-w-none w-[9%] h-auto top-[36.4%] left-[65%] lg:top-[85.2%] lg:left-[30.5%] lg:h-[5%] lg:w-auto text-green-600" />

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

	<a class="relative lg:top-[40%] lg:right-[77%] lg:w-[20%] lg:h-[17%]" href="/artists/tatterjae"><Icon name="arrow-left-outline" class="relative hidden lg:flex lg:w-[100%] lg:h-[100%] text-white" /></a>
	<a class="relative lg:top-[40%] lg:left-[21%] lg:w-[20%] lg:h-[17%]" href="/artists/domthekidtattoos"><Icon name="arrow-right-outline" class="relative hidden lg:flex lg:w-[100%] lg:h-[100%] text-white" /></a>
</div>

