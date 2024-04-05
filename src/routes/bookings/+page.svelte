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

	// Upload/loading for image inconsistently uploading

	//Value bindings
	let firstName : string; //Creates strange bug in not loading in page elements. Probably has to be moved to inside the HTML
	let lastName : string;

	let dateOfBirth : string;
	let pronouns : string;
	let email : string;
	let insta : string;
	let phone : string;

	let selectedNewReturning : string;
	let selectedSilent : string;
	let selectedArtist : string;
	let ageConfirm = false;

	onMount(() => {
		firstName = sessionStorage.getItem("firstName") || "";
		lastName = sessionStorage.getItem("lastName") || "";
		dateOfBirth = sessionStorage.getItem("dateOfBirth") || "";
		underageCheck();
		pronouns = sessionStorage.getItem("pronouns") || "";
		email = sessionStorage.getItem("email") || "";
		insta = sessionStorage.getItem("insta") || "";
		phone = sessionStorage.getItem("phone") || "";

		selectedNewReturning = sessionStorage.getItem("selectedNewReturning") || "";
		selectedSilent = sessionStorage.getItem("selectedSilent") || "";
		selectedArtist = sessionStorage.getItem("selectedArtist") || "";

		available_time.early = JSON.parse(sessionStorage.getItem("early") || "false");
		available_time.late = JSON.parse(sessionStorage.getItem("late") || "false");

		available_days.monday = JSON.parse(sessionStorage.getItem("monday") || "false");
		available_days.tuesday = JSON.parse(sessionStorage.getItem("tuesday") || "false");
		available_days.wednesday = JSON.parse(sessionStorage.getItem("wednesday") || "false");
		available_days.thursday = JSON.parse(sessionStorage.getItem("thursday") || "false");
		available_days.friday = JSON.parse(sessionStorage.getItem("friday") || "false");
		available_days.saturday = JSON.parse(sessionStorage.getItem("saturday") || "false");
		available_days.sunday = JSON.parse(sessionStorage.getItem("sunday") || "false");

		tattoo_style.color = JSON.parse(sessionStorage.getItem("color") || "false");
		tattoo_style.black_and_grey = JSON.parse(sessionStorage.getItem("black_and_grey") || "false");
		tattoo_style.fine_line = JSON.parse(sessionStorage.getItem("fine_line") || "false");
		tattoo_style.other = JSON.parse(sessionStorage.getItem("other") || "false");

		tattoo_design = sessionStorage.getItem("tattoo_design") || "";
		design_placement = sessionStorage.getItem("design_placement") || "";
		tattoo_size = sessionStorage.getItem("tattoo_size") || "";
		
		selectedExistingTattoos = sessionStorage.getItem("selectedExistingTattoos") || "";
		selectedCoverup = sessionStorage.getItem("selectedCoverup") || "";
		selectedScarring = sessionStorage.getItem("selectedScarring") || "";

		allergies = sessionStorage.getItem("allergies") || "";
		eventCode = sessionStorage.getItem("eventCode") || "";
		selectedAntibiotics = sessionStorage.getItem("selectedAntibiotics") || "";
	})

	function birthdayValid()
	{
		let splitDOB = dateOfBirth.split("-")
		let currentDate = new Date();
		if(currentDate.getFullYear() - parseInt(splitDOB[0]) < 18)
			return false;
		if(currentDate.getFullYear() - parseInt(splitDOB[0]) == 18 && (currentDate.getMonth() + 1) < parseInt(splitDOB[1]))
			return false;
		if(currentDate.getFullYear() - parseInt(splitDOB[0]) == 18 && (currentDate.getMonth() + 1) == parseInt(splitDOB[1]) && currentDate.getDate() < parseInt(splitDOB[2]))
			return false;
		return true;
	}

	function underageCheck()
	{
		if(dateOfBirth != undefined)
			if(birthdayValid())
				ageConfirm = true;
			else
				ageConfirm = false;
	}

	const available_time = {
		early: false,
		late: false
	}

	const available_days = {
		monday: false,
		tuesday: false,
		wednesday: false,
		thursday: false,
		friday: false,
		saturday: false,
		sunday: false
	}

	const tattoo_style = {
		color: false,
		black_and_grey: false,
		fine_line: false,
		other: false
	}
	
	let tattoo_design : string;
	let design_placement : string;
	let tattoo_size : string;

	let selectedExistingTattoos : string;
	let selectedCoverup : string;
	let selectedScarring : string;
	let allergies : string;
	let eventCode : string;
	let selectedAntibiotics : string;

	let area_photo : FileList;
	let reference_photo : FileList;

	let yesNo = [
		{ value: 'yes', name: 'Yes' },
		{ value: 'no', name: 'No' },
	];

	let artists = [
		{ value: 'Any', name: 'First Available/Any'},
		{ value: 'Jasper', name: 'Jasper (@tatterjae)' },
		{ value: 'Carlos', name: 'Carlos (@carlosdotnet)' },
		{ value: 'Dominic', name: 'Dominic (@domthekidtattoos)' }
	];

	let newReturning = [
		{ value: 'new', name: 'New'},
		{ value: 'returning', name: 'Returning' }
	];

	//Text area props
	let textAreaPropsDesign = {
		id: 'message',
		name: 'tattoo_design',
		label: 'Your message',
		rows: 4,
		placeholder: 'Type here...'
	};

	let textAreaPropsPlacement = {
		id: 'message',
		name: 'tattoo_placement',
		label: 'Your message',
		rows: 1,
		placeholder: ''
	};

	let textAreaPropsSize = {
		id: 'message',
		name: 'tattoo_size',
		label: 'Your message',
		rows: 1,
		placeholder: ''
	};

	let textAreaPropsAllergies = {
		id: 'message',
		name: 'allergies',
		label: 'Your message',
		rows: 1,
		placeholder: ''
	};

	let textAreaPropsEvents = {
		id: 'message',
		name: 'event_code',
		label: 'Your message',
		rows: 1,
		placeholder: ''
	};

	let fileuploadprops = {
		id: 'area',
		name: "area"
	};

	let fileuploadprops2 = {
		id: 'reference',
		name: "reference"
	};

	//Validation
	let submitConfirm = false;
	let requiredAppear = false;
	function settingValidity(){
		let valid = true;
		if(!firstName)
			valid = false;
		if(!lastName)
			valid = false;
		if(!dateOfBirth)
			valid = false;
		if(!email)
			valid = false;
		if(!phone)
			valid = false;
		if(!selectedNewReturning)
			valid = false;
		if(!selectedArtist)
			valid = false;
		if(!available_time.early && !available_time.late)
			valid = false;
		if(!available_days.monday && !available_days.tuesday && !available_days.wednesday && !available_days.thursday && !available_days.friday && !available_days.saturday && !available_days.sunday)
			valid = false;
		if(!tattoo_style.color && !tattoo_style.black_and_grey && !tattoo_style.fine_line && !tattoo_style.other)
			valid = false;
		if(!tattoo_design)
			valid = false;
		if(!design_placement)
			valid = false;
		if(!tattoo_size)
			valid = false;
		if(!selectedExistingTattoos)
			valid = false;
		if(!selectedCoverup)
			valid = false;
		if(!selectedScarring)
			valid = false;
		if(!selectedAntibiotics)
			valid = false;
		if(!area_photo)
			valid = false;
		if(!ageConfirm)
			valid = false;
		if(valid)
			submitConfirm = true;
		requiredAppear = true;
	}

	//Add beforeunload that is disabled when executed by submit button
	function beforeunload(event: BeforeUnloadEvent) {
		if(!submitConfirm){
			event.preventDefault();
			return event.returnValue = '';
		}
		else
		{
			return true;
		}
    }

	function saveSessionStorage(field : string, e : Event){
		sessionStorage.setItem(field, (e.target as HTMLInputElement).value);
		// https://freshman.tech/snippets/typescript/fix-value-not-exist-eventtarget/
	}

	function saveCheckboxStorage(field : string, e : Event){
		sessionStorage.setItem(field, JSON.stringify((e.target as HTMLInputElement).checked));
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
	<enhanced:img class="relative -z-10 top-[7vw] left-[8vw] w-[30vw] lg:top-[15vh] lg:left-[43%] lg:w-[18vh]" src={sparkles} alt="contacts-screen"/>
	<enhanced:img class="relative -z-10 bottom-[25vw] left-[64vw] w-[30vw] lg:top-[26vh] lg:left-[3.8%] lg:w-[18vh]" src={sparklesRotated} alt="contacts-screen"/>

	<iframe class="relative overflow-y-scroll w-[95.6vw] h-[75vh] bottom-[32.4vw] left-[2.65vw] lg:w-[79vh] lg:h-[58.8vh] lg:bottom-[7.4vh] lg:left-[20.2vh] -z-20"
			id="appointment"
			title="Appointment Webpage"
			src="https://tattedferret.setmore.com">
	</iframe>
</div>

<svelte:window on:beforeunload={beforeunload}/>