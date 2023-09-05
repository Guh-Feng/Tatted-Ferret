<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
	$: activeUrl = $page.url.pathname;

    let selected = 0;
    function change(val: number)
    {
        selected = val;
    }
</script>

<!--Max height and width changes how much available spacing it has as screen changes not the max size it can be.-->
<img class="absolute left-80 top-0 ml-10 -z-10 max-h-none max-w-none" height="838.5" width="838.5" src="/contact/contact-screen.png" alt="contacts-screen"/>
<div class="flex flex-col absolute left-96 ml-56 top-32 mt-2">
    <button class="flex justify-center" on:click={() => change(0)}><img class="relative top-4 max-h-none max-w-none" src={selected === 0 ? "/contact/address_selected.png" : "/contact/address_unselected.png"} alt="address button" width="55" height="55"></button>
    <button class="flex justify-center" on:click={() => change(1)}><img class="relative left-14 bottom-1 max-h-none max-w-none" src={selected === 1 ? "/contact/phone_selected.png" : "/contact/phone_unselected.png"} alt="address button" width="55" height="55"></button>
    <button class="flex justify-center" on:click={() => change(2)}><img class="relative left-14 top-1 max-h-none max-w-none" src={selected === 2 ? "/contact/email_selected.png" : "/contact/email_unselected.png"} alt="address button" width="55" height="55"></button>
    <button class="flex justify-center" on:click={() => change(3)}><img class="relative bottom-4 max-h-none max-w-none" src={selected === 3 ? "/contact/instagram_selected.png" : "/contact/instagram_unselected.png"} alt="address button" width="55" height="55"></button>
</div>

<div class="absolute w-56 h-28 top-36 ml-80 left-[26em] bg-orange-400 rounded-lg max-96"></div>

{#if selected === 0}
    <img class="absolute w-56 h-24 top-64 ml-80 left-[26em] max-96" src="/contact/address.png" alt="10856 sw 104th st, suite 126, Miami, FL, 33176">
{/if}

{#if selected === 1}
    <img class="absolute w-56 h-16 top-40 mt-2 ml-80 left-[26em] max-96" src="/contact/number.png" alt="studio number: 3057074246">
{/if}

{#if selected === 2}
    <img class="absolute w-56 h-28 top-36 ml-80 left-[26em] max-96" src="/contact/email.png" alt="studio number: 3057074246">
{/if}

{#if selected === 1 || selected === 2}
    <img class="absolute w-56 h-20 top-64 ml-80 left-[26em] max-96" src="/contact/requests.png" alt="For tattoo requests, please fill out our booking form">
{/if}

{#if selected === 3}
    <img class="absolute w-56 top-40 mt-1 ml-80 left-[26em] max-96" src="/contact/instagram.png" alt="studio number: 3057074246">
    <img class="absolute w-56 h-24 top-64 ml-80 left-[26em] max-96" src="/contact/instas.png" alt="For tattoo requests, please fill out our booking form">
{/if}


