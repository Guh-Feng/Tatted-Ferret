<script>
	import '../app.postcss';
	import { page } from '$app/stores';
	$: activeUrl = $page.url.pathname;

	import logoTransparent from '$lib/logo-transparent.png?enhanced'
	import artists from '$lib/artists.png?enhanced'
	import book from '$lib/book.png?enhanced'
	import contact from '$lib/contact.png?enhanced'
	import faq from '$lib/faq.png?enhanced'
</script>

<svelte:head>
	<title>
		Tatted Ferret Tattoos
	</title>
	<meta name="description" content="Looking to get a tattoo? Book now with any of our artists at Tatted Ferret Tattoo Studio, conveniently located across the MDC Kendall Campus.">
</svelte:head>

<enhanced:img class="w-fit mx-auto lg:w-7/12 lg: p-5" src={logoTransparent} alt="Tatted Ferret Logo" />

<div class="mx-auto grid grid-cols-2 gap-y-2 justify-center lg:justify-items-center lg:absolute lg:top-0 lg:grid-cols-4">
    <a href="/artists/tatterjae" class="w-[47.6vw] lg:mr-auto lg:w-10/12 lg:col-start-1 lg:col-span-1"><enhanced:img src={artists} alt="artists"/></a>
    <a href="/bookings" class="lg:ml-auto lg:w-10/12 lg:col-start-4 lg:col-span-1"><enhanced:img src={book} alt="bookings"/></a>
    <a href="/faq" class="w-[47.6vw] lg:mr-auto lg:w-10/12 lg:col-start-1 lg:col-span-1"><enhanced:img src={faq} alt="frequently asked questions"/></a>
    <a href="/contacts" class="relative bottom-[4.5vw] lg:bottom-0 lg:ml-auto lg:w-10/12 lg:col-start-4 lg:col-span-1"><enhanced:img src={contact} alt="contact"/></a>
</div>
