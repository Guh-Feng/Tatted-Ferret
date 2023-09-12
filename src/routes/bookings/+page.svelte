<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
	import { Label, Input, Button, Dropdown, DropdownItem, Select, Checkbox, Textarea, Fileupload } from 'flowbite-svelte';
	import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;

	let selectedYesNo : string;
	let selectedExistingTattoos : string;
	let selectedCoverup : string;
	let selectedScarring : string;
	let selectedAntibiotics : string;

	let yesNo = [
		{ value: 'yes', name: 'Yes' },
		{ value: 'no', name: 'No' },
	];

	let selectedArtist : string;
	let artists = [
		{ value: 'any', name: 'First Available/Any'},
		{ value: 'jasper', name: 'Jasper (@tatterjae)' },
		{ value: 'carlos', name: 'Carlos (@carlosdotnet)' },
		{ value: 'dominic', name: 'Dominic (@domthekidtattoos)' }
	];
	let selectedNewReturning : string;
	let newReturning = [
		{ value: 'new', name: 'New'},
		{ value: 'returning', name: 'Returning' }
	];
	let textareapropsLarge = {
		id: 'message',
		name: 'message',
		label: 'Your message',
		rows: 4,
		placeholder: 'Type here...'
	};
	let textareapropsSmall = {
		id: 'message',
		name: 'message',
		label: 'Your message',
		rows: 1,
		placeholder: ''
	};

	let fileuploadprops = {
		id: 'area'
	};

	let fileuploadprops2 = {
		id: 'reference'
	};
</script>

<img class="absolute left-80 top-0 ml-10 -z-10 max-h-none max-w-none" height="645" width="645" src="/booking/booking.png" alt="contacts-screen"/>


<form class="absolute w-[28.4em] h-[21.4em] top-48 left-[30.5em] overflow-y-scroll">
	<div class="mb-4">
		<Label for="small-input" class="block mb-2">Name</Label>
		<div class="flex w-full">	
			<Input id="small-input" size="sm" class="w-full mx-1" placeholder="First Name" />
			<Input id="small-input" size="sm" class="w-full mx-1" placeholder="Last Name" />
		</div>
	</div>
	<div class="mb-4">
		<Label for="small-input" class="block mb-2">Date of Birth</Label>
		<div class="flex w-full">	
			<Input id="date" name="date" required type="date" class="h-8 w-32" />
		</div>
	</div>
	<div class="mb-4">
		<Label for="small-input" class="block mb-2">Pronouns</Label>
		<div class="flex w-full">	
			<Input id="small-input" size="sm" class="w-full mx-1" placeholder="" />
		</div>
	</div>
	<div class="mb-4">
		<Label for="small-input" class="block mb-2">Email</Label>
		<div class="flex w-full">	
			<Input id="small-input" size="sm" class="w-full mx-1" placeholder="example@example.com" />
		</div>
	</div>
	<div class="mb-4">
		<Label for="small-input" class="block mb-2">Instagram Handle</Label>
		<div class="flex w-full">	
			<Input id="small-input" size="sm" class="w-full mx-1" placeholder="" />
		</div>
	</div>
	<div class="mb-4">
		<Label for="small-input" class="block mb-1">Phone Number</Label>
		<div class="flex w-full">	
			<Input id="small-input" size="sm" class="w-full mx-1" placeholder="(000)-000-0000" />
		</div>
	</div>

	<Label class="mb-4">
		New or Returning Client:
		<Select class="mt-2" items={newReturning} bind:value={selectedNewReturning} />
	</Label>

	<Label class="mb-4">
		Do you want a "silent" appointment?
		<Select class="mt-2" items={yesNo} bind:value={selectedYesNo} />
	</Label>
	
	<Label class="mb-4">
		Preferred Artist:
		<Select class="mt-2" items={artists} bind:value={selectedArtist} />
	</Label>

	<Label class="mb-4">
		Availability:
		<Checkbox class="my-2 ml-2">11:30 am - 3:00 pm</Checkbox>
		<Checkbox class="ml-2">3:30 pm - 7:00 pm</Checkbox>
	</Label>

	<Label class="mb-4">
		Availability - please select ALL days of the week that apply. Please keep in mind that not all artists work all of these days, but some are flexible:
		<Checkbox class="my-2 ml-2">Monday</Checkbox>
		<Checkbox class="my-2 ml-2">Tuesday</Checkbox>
		<Checkbox class="my-2 ml-2">Wednesday</Checkbox>
		<Checkbox class="my-2 ml-2">Thursday</Checkbox>
		<Checkbox class="my-2 ml-2">Friday</Checkbox>
		<Checkbox class="my-2 ml-2">Saturday</Checkbox>
		<Checkbox class="ml-2">Sunday</Checkbox>
	</Label>

	<Label class="mb-4">
		Tattoo Design Info - Please select a style:
		<Checkbox class="my-2 ml-2">Color</Checkbox>
		<Checkbox class="my-2 ml-2">Black and Grey</Checkbox>
		<Checkbox class="my-2 ml-2">Fine Line</Checkbox>
		<Checkbox class="ml-2">Other</Checkbox>
	</Label>

	<Label class="mb-4">
		Tattoo Design Description: 
		<Textarea class="mt-2" {...textareapropsLarge} />
	</Label>

	<Label class="mb-4">
		Tattoo Design Placement:
		<Textarea class="mt-2" {...textareapropsSmall} />
	</Label>

	<Label class="mb-4">
		Tattoo Design Size
		<Textarea class="mt-2" {...textareapropsSmall} />
	</Label>

	<Label class="mb-4">
		Working around existing tattoos?
		<Select class="mt-2" items={yesNo} bind:value={selectedExistingTattoos} />
	</Label>

	<Label class="mb-4">
		Is this tattoo a coverup?
		<Select class="mt-2" items={yesNo} bind:value={selectedCoverup} />
	</Label>

	<Label class="mb-4">
		Tattooing over scarring?
		<Select class="mt-2" items={yesNo} bind:value={selectedScarring} />
	</Label>

	<Label class="mb-4">
		Allergies or Skin Conditions?
		<Textarea class="mt-2" {...textareapropsSmall} />
	</Label>

	<Label class="mb-4">
		Are you currently on antibiotics?
		<Select class="mt-2" items={yesNo} bind:value={selectedAntibiotics} />
	</Label>

	<Label class="pb-2">Photo(s) of area to be tattooed:</Label>
	<Fileupload {...fileuploadprops} />

	<Label class="pb-2">Reference and/or inspo photo(s):</Label>
	<Fileupload {...fileuploadprops2} />
</form>