<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
    import { Icon } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;

    let selected = 0;
    function change(val: number)
    {
        selected = val;
    }
</script>

<img class="absolute left-96 ml-32 top-0 -z-10 max-h-none max-w-none" height="510" width="510" src="/faq/questions.png" alt="faq section"/>
<div class="absolute left-96 ml-40 w-96 h-96 top-32 mt-2">
    <div class="flex flex-col">
        <button on:click={() => change(1)} aria-label="question one: Do you take walkins?" on:click={() => change(1)}><div class="h-9"></div></button>
        <button on:click={() => change(2)} aria-label="question two: When are you open?" on:click={() => change(2)}><div class="h-9"></div></button>
        <button on:click={() => change(3)} aria-label="question three: How much will a tattoo cost?" on:click={() => change(3)}><div class="h-8"></div></button>
        <button on:click={() => change(4)} aria-label="question four: How do I take care of my tattoo?" class="w-80" on:click={() => change(4)}><div class="h-[65px] w-80"></div></button>
        <button on:click={() => change(5)} aria-label="question five: Do you do piercings?" class="w-80" on:click={() => change(5)}><div class="h-9 w-80"></div></button>
        <button on:click={() => change(6)} aria-label="question six: Do you tattoo minors?" class="w-80" on:click={() => change(6)}><div class="h-9 w-80"></div></button>
        <button on:click={() => change(7)} aria-label="question seven: I don't have any tattoos, can you walk me through the process" on:click={() => change(7)}><div class="h-[65px]"></div></button>
        <button on:click={() => change(8)} aria-label="question eight: I have/potentially have a medical condition, can I still get a tattoo" on:click={() => change(8)}><div class="h-[70px]"></div></button>
    </div>
</div>

<div class="absolute left-56 top-0 ml-24">
    <button on:click={() => change(0)}><Icon name="close-outline" class="{selected > 0 ? "" : "hidden"} z-10 absolute {selected > 6 ? "top-12" : "top-20"} mt-4 left-52 mx-20 w-7 h-7 text-orange-200" /></button>
    <img src="/faq/one.png" class="{selected == 1 ? "" : "hidden"} max-h-none max-w-none" alt="1. Yes we do! Although appointments are preferred so we recommend calling ahead if you plan to stop by." height="600" width="600"/>
    <img src="/faq/two.png" class="{selected == 2 ? "" : "hidden"} max-h-none max-w-none" alt="2. Our studio hours are 12 pm - 7 pm, Monday - Saturday. Keep in mind our artists don't have fixed work schedules so the studio might not always be open during these hours." height="600" width="600"/>
    <img src="/faq/three.png" class="{selected == 3 ? "" : "hidden"} relative -top-2 max-h-none max-w-none" alt="3. Our shop minimum is $60, so the price goes up from there. The cost of a tattoo can vary greatly depending on the size, style, the artist's skill set/experience, etc. therefore, price quotes can only be given after a consultation." height="600" width="600"/>
    <img src="/faq/four.png" class="{selected == 4 ? "" : "hidden"} max-h-none max-w-none" alt="4. See instructions below for aftercare instructions" height="600" width="600"/>
    <img src="/faq/five.png" class="{selected == 5 ? "" : "hidden"} max-h-none max-w-none" alt="5. We do not do piercings at this time." height="600" width="600"/>
    <img src="/faq/six.png" class="{selected == 6 ? "" : "hidden"} max-h-none max-w-none" alt="6. We do not tattoo minors." height="600" width="600"/>
    <img src="/faq/seven.png" class="{selected == 7 ? "" : "hidden"} relative left-2 -top-5 max-h-none max-w-none" alt="7. Sure! We'll list out the general steps for our studio: 1. Fill out booking form, 2. We'll reach out for further information or to schedule an in-person consultation, 3. If you decide to proceed with your artist, we require a nonrefundable deposit when you schedule a date for your appointment. It will count towards the total cost of the tattoo, 4. On the day of the appointment, you'll fill out a consent form and we'll ask to check valid photo ID to verify your age, 5. Your artist will prep your skin by shaving and cleaning the area before applying a stencil, 6. Once you approve the size and placement of the stencil, your artist will wait for the stencil to dry before starting. Your artist will check in on you occasionally throughout the tattooing process but if at any point you need to stop, please notify the artist, we prioritize your wellbeing, 7. Once your tattoo is done, your artist will cover it with a transparent derm shield and go over aftercare, 9. You pay the remainder of the cost and leave with a new tattoo!" height="570" width="570"/>
    <img src="/faq/eight.png" class="{selected == 8 ? "" : "hidden"} relative left-3 -top-4 max-h-none max-w-none" alt="8. We are not medical professionals and always advise consulting with one if you have any concerns about getting a tattoo. If your provider has greenlit the procedure, then we're more than happy to discuss any accommodations we can make to help you have a more comfortable and safe experience. If your concerns are allergy related, you are welcome to ask us for the products we use to look through the ingredients or, depending on the product, we can provide a sample for you to test on your skin." height="550" width="550"/>
</div>