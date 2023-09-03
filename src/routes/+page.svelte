<script>
	import '../app.postcss';
	import { page } from '$app/stores';
	$: activeUrl = $page.url.pathname;
</script>

<div class="flex-col w-fit mx-auto">
    <img class="-my-20" src="logo-transparent.png" alt="Tatted Ferret Logo" height="550" width="550">
</div>
<div class="flex justify-evenly mt-8 mx-40">
    <a href="/artists/tatterjae" class="flex justify-center"><img src="artists.png" alt="artists" width="150" height="150"/></a>
    <a href="/bookings" class="flex justify-center"><img src="book.png" alt="bookings" width="150" height="150"/></a>
    <a href="/faq" class="flex justify-center"><img src="faq.png" alt="frequently asked questions" width="150" height="150"/></a>
    <a href="/contacts" class="flex justify-center"><img src="contact.png" alt="contact" width="150" height="150"/></a>
</div>