<script>
	import '../../../app.postcss';
	import { page } from '$app/stores';
    import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;

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

<a href="https://instagram.com/carlosdotnet?igshid=MmU2YjMzNjRlOQ==" target="_blank"><img class="absolute left-96 top-0 -z-10 max-h-none max-w-none select-none" height="647" width="647" src="../artists/carlosdotnet.png" alt="instagram screen"/></a>

<img class="absolute left-[41.5em] top-[10.6em] select-none" height="200" width="200" src="../artists/carlos/carlos{imageSelection}.png" alt="slideshow of tattoos">
<Icon name="arrow-left-outline" on:click={() => decrement()} class="absolute top-[30.2em] left-[36.6em] mx-20 w-8 h-8 text-orange-600" />
<Icon name="arrow-right-outline" on:click={() => increment()} class="absolute top-[30.2em] left-[46.7em] mx-20 w-8 h-8 text-orange-600" />
<p class="absolute top-[21.5em] left-[41.6em] select-none">
	<span class="{imageSelection == 1 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 2 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 3 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 4 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 5 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 6 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 7 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 8 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 9 ? "text-black" : "text-white"} text-7xl select-none">.</span>
	<span class="{imageSelection == 10 ? "text-black" : "text-white"} text-7xl select-none">.</span>
</p>

<a href="/artists/tatterjae"><Icon name="arrow-left-outline" class="absolute top-60 mt-4 left-52 mx-20 w-20 h-20 text-white" /></a>
<a href="/artists/domthekidtattoos"><Icon name="arrow-right-outline" class="absolute top-60 mt-4 left-[42rem] ml-96 w-20 h-20 text-white" /></a>

