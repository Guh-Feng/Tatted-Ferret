<script>
	import '../app.postcss';
	import { page } from '$app/stores';
	import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;

	//Can click through the background to the instagram page
	//Accessibility, form, optimization, and background pass

	let openMenu = false;
	function displayMenu()
	{
		openMenu = !openMenu;
	}
</script>

<style>
:global(body) {
	background-color: orange;
	color: #0084f6;
	transition: background-color 0.3s
}
</style>

{#if activeUrl != "/"}
<div class='flex flex-col z-30 absolute lg:flex-col lg:top-0 {openMenu ? "bg-orange-400" : "w-0"}'>
	<button class="flex w-[20vw] mx-[40vw] mt-[1.5vw] py-[3vw] border-4 border-orange-600 rounded-lg lg:hidden" on:click={() => displayMenu()}>
		<Icon name="{openMenu ? "close-outline" : "bars-outline" }" class="mx-auto w-[10vw] h-[10vw] text-orange-600" />
	</button>
	<div class="lg:flex {openMenu ? "" : "hidden" } lg:flex-col lg:items-center transparent lg:w-[33vh] lg:mx-3">
		<div class="lg:absolute lg:top-[10vh] lg:py-[44vh] lg:px-[7vh] lg:bg-orange-400 lg:rounded-full lg:-z-10"></div>
		<a href="/" class="lg:flex hidden w-[33vh]"><img src="../logo-transparent.png" alt="tatted ferret logo" class="select-none"/></a>
		<div class="mx-auto grid grid-cols-2 gap-y-2 align-middle z-10 lg:grid-cols-1 bg-orange-400 lg:bg-transparent">
			<a href="/artists/tatterjae" class="w-[47.6vw] {activeUrl == "/artists/tatterjae" || activeUrl == "/artists/carlosdotnet" || activeUrl == "/artists/domthekidtattoos" ? "relative lg:left-10" : ""} lg:w-[17vh] "><img src="../artists.png" alt="artists" class="select-none"/></a>
			<a href="/bookings" class="{activeUrl == "/bookings" ? "relative lg:left-10" : ""} lg:w-[17vh] "><img src="../book.png" alt="bookings" class="select-none"/></a>
			<a href="/faq" class="w-[47.6vw] {activeUrl == "/faq" ? "relative lg:left-10" : ""} lg:w-[17vh] "><img src="../faq.png" alt="frequently asked questions" class="select-none"/></a>
			<a href="/contacts" class="relative bottom-[4.5vw] {activeUrl == "/contacts" ? "lg:left-10" : ""} lg:w-[17vh] lg:bottom-0"><img src="../contact.png" alt="contact" class="select-none"/></a>
		</div>
	</div>
</div>

{/if}

<slot />
