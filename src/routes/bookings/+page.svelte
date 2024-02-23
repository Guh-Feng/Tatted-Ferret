<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
	import { Label, Input, Button, Select, Checkbox, Textarea, Fileupload } from 'flowbite-svelte';
	import { onMount } from 'svelte';
	$: activeUrl = $page.url.pathname;

	// 18th birthday tattoos?
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
	// function beforeunload(event: BeforeUnloadEvent) {
    //     event.preventDefault();
    //     return event.returnValue = '';
    // }

	function saveSessionStorage(field : string, e : Event){
		sessionStorage.setItem(field, (e.target as HTMLInputElement).value);
		// https://freshman.tech/snippets/typescript/fix-value-not-exist-eventtarget/
	}

	function saveCheckboxStorage(field : string, e : Event){
		sessionStorage.setItem(field, JSON.stringify((e.target as HTMLInputElement).checked));
	}
</script>

<img class="absolute -z-10 hidden lg:flex lg:left-[27vw] lg:w-[110vh] lg:max-h-none lg:max-w-none" src="/booking/booking.png" alt="contacts-screen"/>

<div class="flex flex-col absolute w-screen top-[21vw] -z-20 lg:hidden">
	<img class="" src="/booking/mobile_booking_header.png" alt="contacts-screen"/>
	<img class="flex  h-[75vh]" src="/booking/mobile_booking_body.png" alt="contacts-screen"/>
	<img class="" src="/booking/mobile_booking_footer.png" alt="contacts-screen"/>
</div>

<div class="absolute w-screen -z-10 lg:left-[27vw] lg:w-[110vh] lg:h-[100vh] lg:max-h-none lg:max-w-none">
	<img class="relative -z-10 top-[7vw] left-[8vw] w-[30vw] lg:top-[15vh] lg:left-[43%] lg:w-[18vh]" src="/booking/sparkles.png" alt="contacts-screen"/>
	<img class="relative -z-10 bottom-[25vw] left-[64vw] w-[30vw] lg:top-[26vh] lg:left-[3.8%] lg:w-[18vh]" src="/booking/sparkles_rotated.png" alt="contacts-screen"/>

	<form class="relative overflow-y-scroll w-[95vw] h-[74vh] bottom-[31.5vw] left-[4vw] lg:w-[77.5vh] lg:h-[58.6vh] lg:bottom-[7.3vh] lg:left-[22vh]" action={submitConfirm ? "https://formsubmit.co/tattedferret@gmail.com" : ""} enctype="multipart/form-data" method={submitConfirm ? "POST" : ""}>
		<input type="hidden" name="_subject" value="Form - {selectedArtist}">
		<Label for="small-input" class="block mb-2">Name <span class="text-red-600">*</span></Label>
		<div class="flex w-full mb-4">	
			<Input name="first" id="small-input first" size="sm" class="w-full ml-3 mr-1 {requiredAppear && !firstName ? "border-red-500 bg-red-200" : ""}" placeholder="First Name" bind:value={firstName} on:input={(e) => saveSessionStorage("firstName", e)} />
			<Input name="last" id="small-input last" size="sm" class="w-full mr-3 ml-1 {requiredAppear && !lastName ? "border-red-500 bg-red-200" : ""}" placeholder="Last Name" bind:value={lastName} on:input={(e) => saveSessionStorage("lastName", e)} />
		</div>

		<Label for="small-input" class="block mb-2">Date of Birth <span class="text-red-600">*</span></Label>
		<div class="flex w-full mb-4">
			<Input id="DOB" name="DOB"  type="date" class="h-10 w-32 mx-3 {requiredAppear && !dateOfBirth ? "border-red-500 bg-red-200" : ""}" bind:value={dateOfBirth} on:input={(e) => {underageCheck(); saveSessionStorage("dateOfBirth", e);}} />
		</div>

		{#if dateOfBirth != undefined && !ageConfirm}
			<p class="text-red-600 -mt-4">Must be 18 or older to book.</p>
		{/if}

		<Label for="small-input" class="block mb-2">Pronouns</Label>
		<div class="flex w-full mb-4">	
			<Input name="pronouns" id="small-input" size="sm" class="w-full mx-3" placeholder="" bind:value={pronouns} on:input={(e) => saveSessionStorage("pronouns", e)}/>
		</div>

		<Label for="small-input" class="block mb-2">Email <span class="text-red-600">*</span></Label>
		<div class="flex w-full mb-4">
			<Input name="email" type="email" id="small-input" size="sm" class="w-full mx-3 {requiredAppear && !email ? "border-red-500 bg-red-200" : ""}" placeholder="example@example.com" bind:value={email} on:input={(e) => saveSessionStorage("email", e)} />
		</div>

		<Label for="small-input" class="block mb-2">Instagram Handle</Label>
		<div class="flex w-full mb-4">
			<Input name="instagram_handle" id="small-input" size="sm" class="w-full mx-3" placeholder="" bind:value={insta} on:input={(e) => saveSessionStorage("insta", e)}/>
		</div>

		<Label for="small-input" class="block mb-2">Phone Number <span class="text-red-600">*</span></Label>
		<div class="flex w-full mb-4">	
			<Input name="phone" type="tel" id="small-input" size="sm" class="w-full mx-3 {requiredAppear && !phone ? "border-red-500 bg-red-200" : ""}" placeholder="" bind:value={phone} on:input={(e) => saveSessionStorage("phone", e)} />
		</div>

		<Label class="mb-4">
			New or Returning Client: <span class="text-red-600">*</span>
			<Select name="returning_client" class="mt-2 mx-3 w-6/12 {requiredAppear && !selectedNewReturning ? "border-red-500 bg-red-200" : ""}" items={newReturning} bind:value={selectedNewReturning} on:change={(e) => saveSessionStorage("selectedNewReturning", e)} />
		</Label>

		<Label class="mb-4">
			Do you want a "silent" appointment?
			<Select name="silent_appointment" class="mt-2 mx-3 w-6/12" items={yesNo} bind:value={selectedSilent} on:change={(e) => saveSessionStorage("selectedSilent", e)} />
			<p class="text-xs mx-3">Regardless of the reason, you are welcome to use this option and only necessary conversations will be had, such as placement or color choices.</p>
		</Label>
		
		<Label class="mb-4">
			Preferred Artist: <span class="text-red-600">*</span>
			<Select name="preferred_artist" class="mt-2 mx-3 w-6/12 {requiredAppear && !selectedArtist ? "border-red-500 bg-red-200" : ""}" items={artists} bind:value={selectedArtist} on:change={(e) => saveSessionStorage("selectedArtist", e)} />
		</Label>

		<Label class="mb-4 {requiredAppear && !available_time.early && !available_time.late ? "bg-red-200" : ""}" >
			Availability: <span class="text-red-600">*</span>
				<Checkbox name="early" class="my-2 ml-2" bind:checked={available_time.early} on:change={(e) => saveCheckboxStorage("early", e)}>11:30 am - 3:00 pm</Checkbox>
				<Checkbox name="late" class="ml-2" bind:checked={available_time.late} on:change={(e) => saveCheckboxStorage("late", e)}>3:30 pm - 7:00 pm</Checkbox>
		</Label>

		<Label class="mb-4 {requiredAppear && !available_days.monday && !available_days.tuesday && !available_days.wednesday && !available_days.thursday && !available_days.friday && !available_days.saturday && !available_days.sunday ? "bg-red-200" : ""}">
			Availability - please select ALL days of the week that apply. Please keep in mind that not all artists work all of these days, but some are flexible: <span class="text-red-600">*</span>
			<Checkbox name="monday" class="my-2 ml-2" bind:checked={available_days.monday} on:change={(e) => saveCheckboxStorage("monday", e)}>Monday</Checkbox>
			<Checkbox name="tuesday" class="my-2 ml-2" bind:checked={available_days.tuesday} on:change={(e) => saveCheckboxStorage("tuesday", e)}>Tuesday</Checkbox>
			<Checkbox name="wednesday" class="my-2 ml-2" bind:checked={available_days.wednesday} on:change={(e) => saveCheckboxStorage("wednesday", e)}>Wednesday</Checkbox>
			<Checkbox name="thursday" class="my-2 ml-2" bind:checked={available_days.thursday} on:change={(e) => saveCheckboxStorage("thursday", e)}>Thursday</Checkbox>
			<Checkbox name="friday" class="my-2 ml-2" bind:checked={available_days.friday} on:change={(e) => saveCheckboxStorage("friday", e)}>Friday</Checkbox>
			<Checkbox name="saturday" class="my-2 ml-2" bind:checked={available_days.saturday} on:change={(e) => saveCheckboxStorage("saturday", e)}>Saturday</Checkbox>
			<Checkbox name="sunday" class="ml-2" bind:checked={available_days.sunday} on:change={(e) => saveCheckboxStorage("sunday", e)}>Sunday</Checkbox>
		</Label>

		<Label class="mb-4 {requiredAppear && !tattoo_style.color && !tattoo_style.black_and_grey && !tattoo_style.fine_line && !tattoo_style.other ? "bg-red-200" : ""}">
			Tattoo Design Info - Please select a style: <span class="text-red-600">*</span>
			<Checkbox class="my-2 ml-2" bind:checked={tattoo_style.color} on:change={(e) => saveCheckboxStorage("color", e)}>Color</Checkbox>
			<Checkbox class="my-2 ml-2" bind:checked={tattoo_style.black_and_grey} on:change={(e) => saveCheckboxStorage("black_and_grey", e)}>Black and Grey</Checkbox>
			<Checkbox class="my-2 ml-2" bind:checked={tattoo_style.fine_line} on:change={(e) => saveCheckboxStorage("fine_line", e)}>Fine Line</Checkbox>
			<Checkbox class="ml-2" bind:checked={tattoo_style.other} on:change={(e) => saveCheckboxStorage("other", e)}>Other</Checkbox>
		</Label>

		<Label class="mb-4">
			Tattoo Design Description: <span class="text-red-600">*</span>
			<Textarea class="mt-2 mx-3 w-11/12 {requiredAppear && !tattoo_design ? "border-red-500 bg-red-200" : ""}" {...textAreaPropsDesign} bind:value={tattoo_design} on:input={(e) => saveSessionStorage("tattoo_design", e)} />
			<p class="text-xs mx-3 -mt-1">Detailed description of design including theme, etc.</p>
		</Label>
		
		<Label class="mb-4">
			Tattoo Design Placement: <span class="text-red-600">*</span>
			<Textarea class="mt-2 mx-3 w-11/12 {requiredAppear && !design_placement ? "border-red-500 bg-red-200" : ""}" {...textAreaPropsPlacement} bind:value={design_placement} on:input={(e) => saveSessionStorage("tattoo_design", e)} />
			<p class="text-xs mx-3 -mt-1">Ex: forearm, inner arm, bicep, thigh, calf, etc.</p>
		</Label>
		
		<Label class="mb-4">
			Tattoo Design Size <span class="text-red-600">*</span>
			<Textarea class="mt-2 mx-3 w-11/12 {requiredAppear && !tattoo_size ? "border-red-500 bg-red-200" : ""}" {...textAreaPropsSize} bind:value={tattoo_size} on:input={(e) => saveSessionStorage("tattoo_size", e)} />
			<p class="text-xs mx-3 -mt-1">Please use inches or centimeters.</p>
		</Label>

		<Label class="mb-4">
			Working around existing tattoos? <span class="text-red-600">*</span>
			<Select name="existing_tattoos" class="mt-2 mx-3 w-6/12 {requiredAppear && !selectedExistingTattoos ? "border-red-500 bg-red-200" : ""}" items={yesNo} bind:value={selectedExistingTattoos} on:input={(e) => saveSessionStorage("selectedExistingTattoos", e)} />
		</Label>

		<Label class="mb-4">
			Is this tattoo a coverup? <span class="text-red-600">*</span>
			<Select name="coverup" class="mt-2 mx-3 w-6/12 {requiredAppear && !selectedCoverup ? "border-red-500 bg-red-200" : ""}" items={yesNo} bind:value={selectedCoverup} on:input={(e) => saveSessionStorage("selectedCoverup", e)} />
		</Label>

		<Label class="mb-4">
			Tattooing over scarring? <span class="text-red-600">*</span>
			<Select name="scarring" class="mt-2 mx-3 w-6/12 {requiredAppear && !selectedScarring ? "border-red-500 bg-red-200" : ""}" items={yesNo} bind:value={selectedScarring} on:input={(e) => saveSessionStorage("selectedScarring", e)} />
		</Label>

		<Label class="mb-3">
			Allergies or Skin Conditions?
			<Textarea class="mt-2 mx-3 w-11/12" {...textAreaPropsAllergies} bind:value={allergies} on:input={(e) => saveSessionStorage("allergies", e)} />
		</Label>

		<Label class="mb-4">
			Event Code
			<Textarea class="mt-2 mx-3 w-11/12" {...textAreaPropsEvents} bind:value={eventCode} on:input={(e) => saveSessionStorage("eventCode", e)} />
		</Label>

		<Label class="mb-4">
			Are you currently on antibiotics? <span class="text-red-600">*</span>
			<Select class="mt-2 mx-3 w-6/12 {requiredAppear && !selectedAntibiotics ? "border-red-500 bg-red-200" : ""}" name="antibiotics" items={yesNo} bind:value={selectedAntibiotics} on:input={(e) => saveSessionStorage("selectedAntibiotics", e)} />
		</Label>

		<Label class="pb-2">Photo(s) of area to be tattooed: <span class="text-red-600">*</span>
			<Fileupload {...fileuploadprops} class="mx-3 w-11/12 {requiredAppear && !area_photo ? "border-red-500 bg-red-200" : ""}" accept="image/png, image/jpeg" bind:files={area_photo} />
		</Label>

		<Label class="pb-2">Reference and/or inspo photo(s):
			<Fileupload {...fileuploadprops2} class="mx-3 w-11/12" accept="image/png, image/jpeg" bind:files={reference_photo} />
		</Label>
		<div class="bg-white mt-8 mr-[5%] overflow-y-scroll h-40">
			<p class="text-black">I understand that I will need to pay a deposit at the time of scheduling the appointment.</p>
			<br />
			<p class="text-black">I understand that my deposit is nonrefundable, nontransferable, and will go towards the cost of the tattoo at the final appointment.</p>
			<br />
			<p class="text-black">I understand that cancellations must be made with at least 48 hours notice, otherwise the deposit will be forfeited.</p>
			<br />
			<p class="text-black">I understand that appointments are rescheduled on a case by case basis, and that clients that no call no show will automatically lose their deposit and will be  to place another deposit for a new appointment. The initial deposit will no longer go towards the cost if a client no call, no shows.</p>
			<br />
			<p class="text-black">I understand that changing a design within 24 hours of the appointment date may result in a rescheduling or cancellation of the tattoo appointment and the quote given initially might change depending on what is changed in the design.</p>
		</div>

		<Checkbox class="my-2 ml-8 mt-5 max-w-none" required>I agree to the terms and conditions <span class="text-red-600">*</span></Checkbox>

		<p class="ml-32 text-red-800">{!submitConfirm && requiredAppear ? "Missing Required Info" : ""}</p>
		<Button on:click={settingValidity} color="red" type="submit" class="relative my-4 mx-[6%] w-40">Submit</Button>
	</form>
</div>

<!-- <svelte:window on:beforeunload={beforeunload}/> -->