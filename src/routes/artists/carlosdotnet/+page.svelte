<script>
	import '../../../app.postcss';
	import { page } from '$app/stores';
    import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;
</script>

<img class="absolute left-96 top-0 -z-10 max-h-none max-w-none" height="647" width="647" src="../artists/instagram_red.png" alt="instagram screen"/>

<a href="/artists/tatterjae"><Icon name="arrow-left-outline" class="absolute top-60 mt-4 left-52 mx-20 w-20 h-20 text-white" /></a>
<a href="/artists/domthekidtattoos"><Icon name="arrow-right-outline" class="absolute top-60 mt-4 left-[42rem] ml-96 w-20 h-20 text-white" /></a>

