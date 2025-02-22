<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
	$: activeUrl = $page.url.pathname;

    //Enhanced image not working with interactive pages as the code is set on compile time, so the images all have to be loaded at the same time.

    import addressSelected from '$lib/contact/address_selected.png?enhanced';
    import addressUnselected from '$lib/contact/address_unselected.png?enhanced';
    import contactScreen from '$lib/contact/contact_screen.png?enhanced';
    import emailSelected from '$lib/contact/email_selected.png?enhanced';
    import emailUnselected from '$lib/contact/email_unselected.png?enhanced';
    import instagramSelected from '$lib/contact/instagram_selected.png?enhanced';
    import instagramUnselected from '$lib/contact/instagram_unselected.png?enhanced';
    import mobileContactScreen from '$lib/contact/mobile_contact_screen.png?enhanced';
    import phoneSelected from '$lib/contact/phone_selected.png?enhanced';
    import phoneUnselected from '$lib/contact/phone_unselected.png?enhanced';

    //Instagram links lead to the instagrams
    //Add font to convert images to selectable text

    let selected = 0;
    function change(val: number)
    {
        selected = val;
    }
</script>

<svelte:head>
	<title>
		contact us
	</title>
	<meta name="description" content="Here are all the ways you can reach us. There's also a helpful map to see where we are.">
</svelte:head>

<!--Max height and width changes how much available spacing it has as screen changes not the max size it can be.-->

<enhanced:img class="absolute hidden lg:flex left-[25%] w-[144.7vh] top-0 -z-10 max-h-none max-w-none" src={contactScreen} alt="contacts-screen"/>
<enhanced:img class="absolute flex lg:hidden w-[100vw] top-[20vw] -z-10 max-h-none max-w-none" src={mobileContactScreen} alt="contacts-screen"/>
<!--Put buttons in separate boxes to move. Move the sidebar. Also don't forget to update bookings.-->
<div class="absolute w-[100vw] top-[30vw] h-[135vw] lg:top-0 lg:left-[25.5%] lg:w-[144.7vh] lg:h-[100vh]">
    <div class="flex flex-col absolute left-[2.5%] top-[21vw] w-[15%] h-[29%] lg:left-[27%] lg:top-[21.5%] lg:h-[40%] lg:w-[10.2%]">
        {#if selected === 0}
            <button class="relative flex justify-center top-[5%] lg:top-[5%] w-[100%] lg:w-[70%]" on:click={() => null}><enhanced:img src={addressSelected} alt="address select"></button>
        {:else}
            <button class="relative flex justify-center top-[5%] lg:top-[5%] w-[100%] lg:w-[70%]" on:click={() => change(0)}><enhanced:img src={addressUnselected} alt="address unselect"></button>
        {/if}
        {#if selected === 1}
            <button class="relative flex justify-center left-[62%] lg:left-[62%] bottom-[1.5%] lg:bottom-[1.5%] w-[100%] lg:w-[70%]" on:click={() => null}><enhanced:img src={phoneSelected} alt="phone select"></button>
        {:else}
            <button class="relative flex justify-center left-[62%] lg:left-[62%] bottom-[1.5%] lg:bottom-[1.5%] w-[100%] lg:w-[70%]" on:click={() => change(1)}><enhanced:img src={phoneUnselected} alt="phone unselect"></button>
        {/if}
        {#if selected === 2}
            <button class="relative flex justify-center left-[62%] lg:left-[62%] top-[1.5%] lg:top-[1.5%] w-[100%] lg:w-[70%]" on:click={() => null}><enhanced:img src={emailSelected} alt="email select"></button>
        {:else}
            <button class="relative flex justify-center left-[62%] lg:left-[62%] top-[1.5%] lg:top-[1.5%] w-[100%] lg:w-[70%]" on:click={() => change(2)}><enhanced:img src={emailUnselected} alt="email unselect"></button>
        {/if}
        {#if selected === 3}
            <button class="relative flex justify-center bottom-[5%] lg:bottom-[5%] w-[100%] lg:w-[70%]" on:click={() => null}><enhanced:img src={instagramSelected} alt="instagram select"></button>
        {:else}
            <button class="relative flex justify-center bottom-[5%] lg:bottom-[5%] w-[100%] lg:w-[70%]" on:click={() => change(3)}><enhanced:img src={instagramUnselected} alt="instagram unselect"></button>
        {/if}
    </div>

    <div class="absolute w-[59vw] h-[28vw] top-[18%] left-[36%] lg:w-[38vh] lg:h-[20vh] lg:top-[24%] lg:left-[44%] bg-orange-400 rounded-[5%]"></div>

    {#if selected === 0}
        <iframe class="relative left-[35%] top-[17.5%] w-[61%] h-[22%] lg:left-[42.6%] lg:top-[23.5%] lg:w-[28%] lg:h-[21%]" title="Tatted Ferret Location" style="border:0" loading="lazy" allowfullscreen referrerpolicy="no-referrer-when-downgrade"
            src="https://www.google.com/maps/embed/v1/place?key=AIzaSyAkaBasDIjIOFgV-Rnu-kpfHQzCRD65uu8
            &q=Tatted Ferret Tattoo Studio"></iframe>
        <p class="relative top-[20%] w-[60%] left-[36%] text-[5.4vw]/[5.4vw] lg:top-[25%] lg:w-[30%] lg:left-[42%] lg:text-[4vh]/[5vh] font-lickorishe text-orange-600 text-center">
            9290 Hammocks Blvd<br>Ste 402-B<br>Miami, FL, 33196
        </p>
    {/if}
 
    {#if selected === 1}
        <p class="relative top-[24%] w-[60%] left-[35.5%] text-[6vw]/[6vw] lg:top-[29%] lg:w-[30%] lg:left-[42%] lg:text-[4.4vh]/[5vh] font-lickorishe text-white text-center">
            Studio number<br>786-542-5759
        </p>
        <p class="relative top-[32%] w-[60%] left-[36%] text-[5.7vw]/[5.7vw] lg:w-[30%] lg:top-[35%] lg:left-[42%] lg:text-[3.5vh]/[4vh] font-lickorishe text-orange-600 text-center">
            For tattoo requests,<br>please fill out our<br>booking form.
        </p>
    {/if}

    {#if selected === 2}
        <p class="relative top-[19.7%] w-[60%] left-[35.5%] text-[4.6vw]/[5.5vw] lg:top-[25%] lg:w-[30%] lg:left-[42.2%] lg:text-[3vh]/[4vh] font-lickorishe text-white text-center">
            Studio Email<br>tattedferret@gmail.com<br>Owner Email<br>jasperg262@gmail.com
        </p>
        <p class="relative top-[24.6%] w-[60%] left-[36%] text-[5.7vw]/[5.7vw] lg:w-[30%] lg:top-[29%] lg:left-[42%] lg:text-[3.5vh]/[4vh] font-lickorishe text-orange-600 text-center">
            For tattoo requests,<br>please fill out our<br>booking form.
        </p>
    {/if}

    {#if selected === 3}
    <p class="relative top-[24.5%] w-[60%] left-[35.5%] text-[6vw]/[6vw] lg:top-[30%] lg:w-[30%] lg:left-[42.2%] lg:text-[4vh]/[4.5vh] font-lickorishe text-white text-center">
        Studio Instagram<br>@tattedferret
    </p>
    <p class="relative top-[31.5%] w-[60%] left-[36%] text-[5.2vw]/[5.2vw] lg:w-[30%] lg:top-[36%] lg:left-[42.2%] lg:text-[3vh]/[3.5vh] font-lickorishe text-orange-600 text-center">
        @domthekid.tattoos<br>@gomezink<br>@tatterjae<br>@edgardo_thompson_<br>arttattoo
    </p>
{/if}

</div>

<!--
{#if selected === 1}
    <enhanced:img class="absolute w-56 h-16 top-40 mt-2 ml-80 left-[26em] max-96" src="/contact/number.png" alt="studio number: 3057074246">
{/if}

{#if selected === 2}
    <enhanced:img class="absolute w-56 h-28 top-36 ml-80 left-[26em] max-96" src="/contact/email.png" alt="studio number: 3057074246">
{/if}

{#if selected === 1 || selected === 2}
    <enhanced:img class="absolute w-56 h-20 top-64 ml-80 left-[26em] max-96" src="/contact/requests.png" alt="For tattoo requests, please fill out our booking form">
{/if}

{#if selected === 3}
    <enhanced:img class="absolute w-56 top-40 mt-1 ml-80 left-[26em] max-96" src="/contact/instagram.png" alt="studio number: 3057074246">
    <enhanced:img class="absolute w-56 h-24 top-64 ml-80 left-[26em] max-96" src="/contact/instas.png" alt="For tattoo requests, please fill out our booking form">
{/if}
-->