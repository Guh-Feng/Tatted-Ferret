<script>
	import '../../../app.postcss';
	import { page } from '$app/stores';
    import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;

	let imageSelection = 1;
	//Standardize image ratio of 1 in height to 0.8 in width, variable alts

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

<img class="absolute left-96 -top-[4px] -z-10 max-h-none max-w-none" height="647" width="647" src="../artists/instagram_orange.png" alt="instagram screen"/>

<img class="absolute left-[41.5em] top-[11em]" height="200" width="200" src="../artists/jae/jae{imageSelection}.png" alt="slideshow of tattoos">
<Icon name="arrow-left-outline" on:click={() => decrement()} class="absolute top-[30.15em] left-[36.6em] mx-20 w-8 h-8 text-black" />
<Icon name="arrow-right-outline" on:click={() => increment()} class="absolute top-[30.15em] left-[46.7em] mx-20 w-8 h-8 text-black" />

<a href="/artists/domthekidtattoos"><Icon name="arrow-left-outline" class="absolute top-60 mt-4 left-52 mx-20 w-20 h-20 text-white" /></a>
<a href="/artists/carlosdotnet"><Icon name="arrow-right-outline" class="absolute top-60 mt-4 left-[42rem] ml-96 w-20 h-20 text-white" /></a>
