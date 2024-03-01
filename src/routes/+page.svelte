<script>
	import '../app.postcss';
	import { page } from '$app/stores';
	$: activeUrl = $page.url.pathname;
</script>

<svelte:head>
	<title>
		tatted ferret
	</title>
	<meta name="description" content="Looking to get a tattoo? Book now with any of our artists at Tatted Ferret Tattoo Studio, conveniently located across the MDC Kendall Campus.">
</svelte:head>

<img class="w-fit mx-auto lg:w-7/12 lg: p-5" src="logo-transparent.png" alt="Tatted Ferret Logo">

<div class="mx-auto grid grid-cols-2 gap-y-2 justify-center lg:justify-items-center lg:absolute lg:top-0 lg:grid-cols-4">
    <a href="/artists/tatterjae" class="w-[47.6vw] lg:mr-auto lg:w-10/12 lg:col-start-1 lg:col-span-1"><img src="artists.png" alt="artists"/></a>
    <a href="/bookings" class="lg:ml-auto lg:w-10/12 lg:col-start-4 lg:col-span-1"><img src="book.png" alt="bookings"/></a>
    <a href="/faq" class="w-[47.6vw] lg:mr-auto lg:w-10/12 lg:col-start-1 lg:col-span-1"><img src="faq.png" alt="frequently asked questions"/></a>
    <a href="/contacts" class="relative bottom-[4.5vw] lg:bottom-0 lg:ml-auto lg:w-10/12 lg:col-start-4 lg:col-span-1"><img src="contact.png" alt="contact"/></a>
</div>
