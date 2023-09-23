<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
	import { Label, Input, Button, Dropdown, DropdownItem, Select, Checkbox, Textarea, Fileupload, Card } from 'flowbite-svelte';
	import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;

	// Include validation and check that checkboxes functions properly or if it needs seperate validation
	// and write the small text notes. Test each  option individually, especially the  labels
	// on checkboxes.
	// Try using props to allow submit to the email form through custom validation https://formsubmit.co/guh.feng@gmail.com

	//Value bindings
	let firstName : string;
	let lastName : string;

	let dateOfBirth : string;
	let pronouns : string;
	let email : string;
	let insta : string;
	let phone : string;

	let selectedNewReturning : string;
	let selectedSilent : string;
	let selectedArtist : string;

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
	let selectedAntibiotics : string;

	let area_photo : FileList;
	let reference_photo : FileList;

	let yesNo = [
		{ value: 'yes', name: 'Yes' },
		{ value: 'no', name: 'No' },
	];

	let artists = [
		{ value: 'any', name: 'First Available/Any'},
		{ value: 'jasper', name: 'Jasper (@tatterjae)' },
		{ value: 'carlos', name: 'Carlos (@carlosdotnet)' },
		{ value: 'dominic', name: 'Dominic (@domthekidtattoos)' }
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

	let fileuploadprops = {
		id: 'area',
		name: "area"
	};

	let fileuploadprops2 = {
		id: 'reference',
		name: "area"
	};

	//Validation
	let submitConfirm = false;
	let requiredAppear = false;
	function settingValidity(){
		console.log("potato")
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
		if(!allergies)
			valid = false;
		if(!selectedAntibiotics)
			valid = false;
		if(!area_photo)
			valid = false;
		if(!reference_photo)
			valid = false;
		if(valid)
			submitConfirm = true;
		requiredAppear = true;
	}
</script>

<img class="absolute left-80 top-0 ml-10 -z-10 max-h-none max-w-none" height="645" width="645" src="/booking/booking.png" alt="contacts-screen"/>

<form class="absolute w-[28.4em] h-[21.4em] top-48 left-[30.5em] overflow-y-scroll" action={submitConfirm ? "https://formsubmit.co/guh.feng@gmail.com" : ""} method={submitConfirm ? "POST" : ""}>

	<Label for="small-input" class="block mb-4">Name</Label>
	<div class="flex w-full mb-4">	
		<Input name="first_name" id="small-input" size="sm" class="w-full mx-1 {requiredAppear && !firstName ? "border-red-500 bg-red-200" : ""}" placeholder="First Name" bind:value={firstName} />
		<Input name="last_name" id="small-input" size="sm" class="w-full mx-1 {requiredAppear && !lastName ? "border-red-500 bg-red-200" : ""}" placeholder="Last Name" bind:value={lastName} />
	</div>

	<Label for="small-input" class="block mb-2">Date of Birth</Label>
	<div class="flex w-full mb-4">
		<Input id="date" name="date"  type="date" class="h-8 w-32 {requiredAppear && !dateOfBirth ? "border-red-500 bg-red-200" : ""}" bind:value={dateOfBirth}/>
	</div>

	<Label for="small-input" class="block mb-2">Pronouns</Label>
	<div class="flex w-full mb-4">	
		<Input name="pronouns" id="small-input" size="sm" class="w-full mx-1" placeholder="" bind:value={pronouns}/>
	</div>

	<Label for="small-input" class="block mb-2">Email</Label>
	<div class="flex w-full mb-4">
		<Input name="email" id="small-input" size="sm" class="w-full mx-1 {requiredAppear && !email ? "border-red-500 bg-red-200" : ""}" placeholder="example@example.com" bind:value={email}/>
	</div>

	<Label for="small-input" class="block mb-2">Instagram Handle</Label>
	<div class="flex w-full mb-4">
		<Input name="instagram_handle" id="small-input" size="sm" class="w-full mx-1" placeholder="" bind:value={insta}/>
	</div>

	<Label for="small-input" class="block mb-2">Phone Number</Label>
	<div class="flex w-full mb-4">	
		<Input name="phone" id="small-input" size="sm" class="w-full mx-1 {requiredAppear && !phone ? "border-red-500 bg-red-200" : ""}" placeholder="000-000-0000" bind:value={phone}/>
	</div>

	<Label class="mb-4">
		New or Returning Client:
		<Select name="returning_client" class="mt-2 {requiredAppear && !selectedNewReturning ? "border-red-500 bg-red-200" : ""}" items={newReturning} bind:value={selectedNewReturning}  />
	</Label>

	<Label class="mb-4">
		Do you want a "silent" appointment?
		<Select name="silent_appointment" class="mt-2" items={yesNo} bind:value={selectedSilent} />
	</Label>
	
	<Label class="mb-4">
		Preferred Artist:
		<Select name="preferred_artist" class="mt-2 {requiredAppear && !selectedArtist ? "border-red-500 bg-red-200" : ""}" items={artists} bind:value={selectedArtist}  />
	</Label>

	<Label class="mb-4 {requiredAppear && !available_time.early && !available_time.late ? "bg-red-200" : ""}" >
		Availability:
			<Checkbox name="available_time" class="my-2 ml-2" bind:checked={available_time.early}>11:30 am - 3:00 pm</Checkbox>
			<Checkbox name="available_time" class="ml-2" bind:checked={available_time.late}>3:30 pm - 7:00 pm</Checkbox>
	</Label>

	<Label class="mb-4 {requiredAppear && !available_days.monday && !available_days.tuesday && !available_days.wednesday && !available_days.thursday && !available_days.friday && !available_days.saturday && !available_days.sunday ? "bg-red-200" : ""}">
		Availability - please select ALL days of the week that apply. Please keep in mind that not all artists work all of these days, but some are flexible:
		<Checkbox name="available_monday" class="my-2 ml-2" bind:checked={available_days.monday}>Monday</Checkbox>
		<Checkbox name="available_tuesday" class="my-2 ml-2" bind:checked={available_days.tuesday}>Tuesday</Checkbox>
		<Checkbox name="available_wednesday" class="my-2 ml-2" bind:checked={available_days.wednesday}>Wednesday</Checkbox>
		<Checkbox name="available_thursday" class="my-2 ml-2" bind:checked={available_days.thursday}>Thursday</Checkbox>
		<Checkbox name="available_friday" class="my-2 ml-2" bind:checked={available_days.friday}>Friday</Checkbox>
		<Checkbox name="available_saturday" class="my-2 ml-2" bind:checked={available_days.saturday}>Saturday</Checkbox>
		<Checkbox name="available_sunday" class="ml-2" bind:checked={available_days.sunday}>Sunday</Checkbox>
	</Label>

	<Label class="mb-4 {requiredAppear && !tattoo_style.color && !tattoo_style.black_and_grey && !tattoo_style.fine_line && !tattoo_style.other ? "bg-red-200" : ""}">
		Tattoo Design Info - Please select a style:
		<Checkbox class="my-2 ml-2" bind:checked={tattoo_style.color}>Color</Checkbox>
		<Checkbox class="my-2 ml-2" bind:checked={tattoo_style.black_and_grey}>Black and Grey</Checkbox>
		<Checkbox class="my-2 ml-2" bind:checked={tattoo_style.fine_line}>Fine Line</Checkbox>
		<Checkbox class="ml-2" bind:checked={tattoo_style.other}>Other</Checkbox>
	</Label>

	<Label class="mb-4">
		Tattoo Design Description: 
		<Textarea class="mt-2 {requiredAppear && !tattoo_design ? "border-red-500 bg-red-200" : ""}" {...textAreaPropsDesign} bind:value={tattoo_design} />
	</Label>

	<Label class="mb-4">
		Tattoo Design Placement:
		<Textarea class="mt-2 {requiredAppear && !design_placement ? "border-red-500 bg-red-200" : ""}" {...textAreaPropsPlacement} bind:value={design_placement} />
	</Label>

	<Label class="mb-4">
		Tattoo Design Size
		<Textarea class="mt-2 {requiredAppear && !tattoo_size ? "border-red-500 bg-red-200" : ""}" {...textAreaPropsSize} bind:value={tattoo_size} />
	</Label>

	<Label class="mb-4">
		Working around existing tattoos?
		<Select name="existing" class="mt-2 {requiredAppear && !selectedExistingTattoos ? "border-red-500 bg-red-200" : ""}" items={yesNo} bind:value={selectedExistingTattoos}  />
	</Label>

	<Label class="mb-4">
		Is this tattoo a coverup?
		<Select name="coverup" class="mt-2 {requiredAppear && !selectedCoverup ? "border-red-500 bg-red-200" : ""}" items={yesNo} bind:value={selectedCoverup}  />
	</Label>

	<Label class="mb-4">
		Tattooing over scarring?
		<Select name="scarring" class="mt-2 {requiredAppear && !selectedScarring ? "border-red-500 bg-red-200" : ""}" items={yesNo} bind:value={selectedScarring}  />
	</Label>

	<Label class="mb-4">
		Allergies or Skin Conditions?
		<Textarea class="mt-2 {requiredAppear && !allergies ? "border-red-500 bg-red-200" : ""}" {...textAreaPropsAllergies} bind:value={allergies} />
	</Label>

	<Label class="mb-4">
		Are you currently on antibiotics?
		<Select class="mt-2 {requiredAppear && !selectedAntibiotics ? "border-red-500 bg-red-200" : ""}" name="antibiotics" items={yesNo} bind:value={selectedAntibiotics}  />
	</Label>

	<Label class="pb-2">Photo(s) of area to be tattooed:
		<Fileupload {...fileuploadprops} class={requiredAppear && !area_photo ? "border-red-500 bg-red-200" : ""} accept="image/png, image/jpeg" bind:files={area_photo} />
	</Label>

	<Label class="pb-2">Reference and/or inspo photo(s):
		<Fileupload {...fileuploadprops2} class={requiredAppear && !reference_photo ? "border-red-500 bg-red-200" : ""} accept="image/png, image/jpeg" bind:files={reference_photo} />
	</Label>
	<div class="bg-white mt-8 mx-4 overflow-y-scroll h-40">
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

	<Checkbox class="my-2 ml-8 mx-20" required>I agree to the terms and conditions</Checkbox>

	<p class="ml-32 text-red-800">{!submitConfirm && requiredAppear ? "Missing Required Info" : ""}</p>
	<Button on:click={settingValidity} color="red" type="submit" class="my-4 mx-32 w-40">Submit</Button>
	

<!-- Debugging Code
	<p>{requiredAppear ? "True?" : "False?"}</p>
	<p>{firstName ? "True" : "False"}</p>
	<p>{lastName ? "True" : "False"}</p>
	<p>{dateOfBirth ? "True" : "False"}</p>
	<p>{email ? "True" : "False"}</p>
	<p>{phone ? "True" : "False"}</p>
	<p>{selectedNewReturning ? "True" : "False"}</p>
	<p>{available_time.early || available_time.late}</p>
	<p>{tattoo_design ? "True" : "False"}</p>
	<p>{design_placement ? "True" : "False"}</p>
	<p>{tattoo_size ? "True" : "False"}</p>
	<p>{selectedExistingTattoos ? "True" : "False"}</p>
	<p>{selectedCoverup ? "True" : "False"}</p>
	<p>{selectedScarring ? "True" : "False"}</p>
	<p>{allergies ? "True" : "False"}</p>
	<p>{selectedAntibiotics ? "True" : "False"}</p>
	<p>{area_photo ? "True" : "False"}</p>
	<p>{reference_photo ? "True" : "False"}</p>
	<p>{submitConfirm ? "True" : "False"}</p>
-->

</form>