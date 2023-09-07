<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
	$: activeUrl = $page.url.pathname;
</script>

<img class="absolute left-80 top-0 ml-10 -z-10 max-h-none max-w-none" height="645" width="645" src="/booking/booking.png" alt="contacts-screen"/>