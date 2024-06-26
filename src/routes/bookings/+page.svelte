<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
	import { Label, Input, Button, Select, Checkbox, Textarea, Fileupload } from 'flowbite-svelte';
	import { onMount } from 'svelte';
	$: activeUrl = $page.url.pathname;

	import booking from '$lib/booking/booking.png?enhanced';
	import mobileBookingBody from '$lib/booking/mobile_booking_body.png?enhanced';
	import mobileBookingFooter from '$lib/booking/mobile_booking_footer.png?enhanced';
	import mobileBookingHeader from '$lib/booking/mobile_booking_header.png?enhanced';
	import sparkles from '$lib/booking/sparkles.png?enhanced';
	import sparklesRotated from '$lib/booking/sparkles_rotated.png?enhanced';
	import bookingTabSelected from '$lib/booking/booking_tab_selected.png?enhanced';
	import merchTab from '$lib/booking/merch_tab.png?enhanced';
	import merchTabSelected from '$lib/booking/merch_tab_selected.png?enhanced';

	let tab = 0;

	//Add beforeunload that is disabled when executed by submit button
	function beforeunload(event: BeforeUnloadEvent) {
			event.preventDefault();
   }

	function handleTab(val: number){
		tab = val;
	}
</script>

<svelte:head>
	<title>
		Book Appointment
	</title>
	<meta name="description" content="Book your appointment with Tatted Ferret Tattoo Studio today.">
</svelte:head>

<enhanced:img class="absolute -z-10 hidden lg:flex lg:left-[27vw] lg:w-[110vh] lg:max-h-none lg:max-w-none" src={booking} alt="contacts-screen"/>

<div class="flex flex-col absolute w-screen top-[21vw] -z-20 lg:hidden">
	<enhanced:img class="" src={mobileBookingHeader} alt="contacts-screen"/>
	<enhanced:img class="flex  h-[75vh]" src={mobileBookingBody} alt="contacts-screen"/>
	<enhanced:img class="" src={mobileBookingFooter} alt="contacts-screen"/>
</div>

<div class="absolute w-screen -z-10 lg:left-[27vw] lg:w-[110vh] lg:h-[100vh] lg:max-h-none lg:max-w-none">
	<enhanced:img class="relative z-20 top-[3vw] left-[9vw] w-[30vw] lg:top-[15vh] lg:left-[65%] lg:w-[18vh]" src={sparkles} alt="contacts-screen"/>
	<enhanced:img class="relative z-20 bottom-[30vw] left-[60vw] w-[30vw] lg:top-[26vh] lg:left-[3.8%] lg:w-[18vh]" src={sparklesRotated} alt="contacts-screen"/>

	<enhanced:img class="relative z-20 w-[35vw] bottom-[32.4vw] left-[2.6vw] lg:w-[24vh] lg:left-[18.3%] lg:bottom-[7.6%]" src={bookingTabSelected} alt="booking tab"/>
	<a href="https://tattedferret-shop.fourthwall.com" target="_blank" ><div class="relative z-30 bottom-[40.7vw] left-[37.5vw] w-[33.65vw] h-[8.5vw] lg:w-[23.5vh] lg:h-[5.9vh] lg:left-[40%] lg:bottom-[13.4%]"></div></a>
	<enhanced:img src={merchTab} alt="booking tab" class="relative z-20 bottom-[49.2vw] left-[37.5vw] w-[33.65vw] lg:left-[40%] lg:bottom-[19.3%] lg:w-[23.5vh]"/>

	<iframe class="relative z-10 overflow-y-scroll w-[95.6vw] h-[75vh] bottom-[57.4vw] left-[2.65vw] lg:w-[79vh] lg:h-[58.8vh] lg:bottom-[24.8vh] lg:left-[20.2vh]"
			id="appointment"
			title="Appointment Webpage"
			src="https://tattedferret.setmore.com">
	</iframe>
</div>

<svelte:window on:beforeunload={beforeunload}/>