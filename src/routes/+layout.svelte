<script>
	import '../app.postcss';
	import { page } from '$app/stores';
	$: activeUrl = $page.url.pathname;
</script>

<style>
:global(body) {
	background-color: orange;
	color: #0084f6;
	transition: background-color 0.3s
}
</style>

{#if activeUrl != "/"}
<div class="flex flex-col transparent w-48 content-center mx-10">
	<div class="absolute py-64 px-10 h-fit bg-orange-400 rounded-full left-24 top-14 -z-10"></div>
  	<a href="/"><img src="../logo-transparent.png" alt="tatted ferret logo" width="200" height="200" class="-my-5"/></a>
	<!--Notably, flexbox is scoped so treat button as a container independent of the overall sidebar*/-->
	<a href="/artists/tatterjae" class="flex justify-center"><img src="../artists.png" alt="artists" width="100" height="100"/></a>
	<a href="/bookings" class="flex justify-center"><img src="../book.png" alt="bookings" width="100" height="100"/></a>
	<a href="/faq" class="flex justify-center"><img src="../faq.png" alt="frequently asked questions" width="100" height="100"/></a>
	<a href="/contacts" class="flex justify-center"><img src="../contact.png" alt="contact" width="100" height="100"/></a>
</div>
{/if}
	
<slot />
