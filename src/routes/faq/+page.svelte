<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
    import { Icon } from 'flowbite-svelte-icons';
    import { Button } from 'flowbite-svelte';
	$: activeUrl = $page.url.pathname;

    import faqBackground from '$lib/faq/faq_background.png';
    import smallAnswer from '$lib/faq/small_answer.png';
    import bigAnswer from '$lib/faq/big_answer.png';

    let selected = 0;
    function change(val: number)
    {
        selected = val;
    }
</script>

<svelte:head>
	<title>
		faq
	</title>
	<meta name="description" content="Here are some commonly asked questions.">
</svelte:head>

<img class="absolute top-[17vw] w-[100vw] lg:top-[0vw] lg:w-[83vh] lg:left-[35vw] -z-10 max-h-none max-w-none" src={faqBackground} alt="faq section"/>

<div class="absolute flex flex-col top-[18vw] left-[1%] w-[99vw] h-[100vh] space-y-[3.2vw] lg:top-[0%] lg:left-[35.2vw] lg:w-[83vh] lg:space-y-[2vh] items-start max-h-none max-w-none">
    <button on:click={() => change(1)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] mt-[31%] select-none">1. Do you take walkins?</button>
    <button on:click={() => change(2)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">2. When are you open?</button>
    <button on:click={() => change(3)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">3. How much will a tattoo cost?</button>
    <button on:click={() => change(4)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">4. How do I take care of </button>
    <button on:click={() => change(4)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">my tattoo?</button>
    <button on:click={() => change(5)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">5. Do you do piercings?</button>
    <button on:click={() => change(6)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">6. Do you tattoo minors?</button>
    <button on:click={() => change(7)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">7. I don't have tattoos, can you </button>
    <button on:click={() => change(7)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">walk me through the process?</button>
    <button on:click={() => change(8)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">8. I have/potentially have a </button>
    <button on:click={() => change(8)} class="font-lickorishe text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] text-orange-600 ml-[5%] select-none">medical condition</button>
</div>

<button on:click={() => change(0)} class="{selected == 1 ? "" : "hidden"} absolute left-[0%] top-[30%] w-fit lg:left-[25%] lg:top-[20%] lg:w-[100vh] h-auto">
    <Icon name="close-outline" class="z-10 absolute mt-[11.5%] left-[47.5%] w-[8%] h-[8%] text-orange-200" />
    <div class="absolute w-[60%] mt-[20.5%] ml-[21%] flex flex-col">
        <p class="font-lickorishe text-[4vw]/[5vw] lg:text-[3.5vh]/[4.96vh] text-orange-600 select-none relative text-left">1. Yes we do! Although appointments are preferred so we recommend calling ahead if you plan to stop by.</p>
    </div>
    <img src={smallAnswer} alt="small answer background" class="w-[100%] max-w-none max-h-none">
</button>

<button on:click={() => change(0)} class="{selected == 2 ? "" : "hidden"} absolute left-[0%] top-[30%] w-fit lg:left-[25%] lg:top-[20%] lg:w-[100vh] h-auto">
    <Icon name="close-outline" class="z-10 absolute mt-[11.5%] left-[47.5%] w-[8%] h-[8%] text-orange-200" />
    <div class="absolute w-[60%] mt-[20.5%] ml-[21%] flex flex-col">
        <p class="font-lickorishe text-[4vw]/[5vw] lg:text-[3.5vh]/[4.96vh] text-orange-600 select-none relative text-left">2. Our studio hours are 12 pm - 7 pm, Monday - Saturday. Keep in mind our artists don't have fixed work schedules so the studio might not always be open during these hours.</p>
    </div>
    <img src={smallAnswer} alt="small answer background" class="w-[100%] max-w-none max-h-none">
</button>

<button on:click={() => change(0)} class="{selected == 3 ? "" : "hidden"} absolute left-[0%] top-[30%] w-fit lg:left-[25%] lg:top-[20%] lg:w-[100vh] h-auto">
    <Icon name="close-outline" class="z-10 absolute mt-[11.5%] left-[47.5%] w-[8%] h-[8%] text-orange-200" />
    <div class="absolute w-[61%] mt-[20.5%] ml-[20.5%] flex flex-col">
        <p class="font-lickorishe text-[3.5vw]/[5vw] lg:text-[3.5vh]/[4.96vh] text-orange-600 select-none relative text-left">3. Our shop minimum is $60. The cost of a tattoo can vary greatly depending on the size, style, the artist's skill set/experience, etc. Therefore, price quotes are only given after a consultation.</p>
    </div>
    <img src={smallAnswer} alt="small answer background" class="w-[100%] max-w-none max-h-none">
</button>

<button on:click={() => change(0)} class="{selected == 4 ? "" : "hidden"} absolute left-[0%] top-[30%] w-fit lg:left-[25%] lg:top-[20%] lg:w-[100vh] h-auto">
    <Icon name="close-outline" class="z-10 absolute mt-[11.5%] left-[47.5%] w-[8%] h-[8%] text-orange-200" />
    <div class="absolute w-[60%] mt-[20.5%] ml-[21%] flex flex-col">
        <p class="font-lickorishe text-[4vw]/[5vw] lg:text-[3.5vh]/[4.96vh] text-orange-600 select-none relative text-left">4. See instructions below for aftercare instructions.</p>
    </div>
    <Button href="https://drive.google.com/file/d/141pxEbyC0BzPPWAM-Ztwj0IB--i36hiv/view?usp=sharing" target="_blank" color="red" type="submit" class="text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] absolute left-[36%] top-[64%] w-[30%] h-[15%]">Attachment</Button>
    <img src={smallAnswer} alt="small answer background" class="w-[100%] max-w-none max-h-none">
</button>

<button on:click={() => change(0)} class="{selected == 5 ? "" : "hidden"} absolute left-[0%] top-[30%] w-fit lg:left-[25%] lg:top-[20%] lg:w-[100vh] h-auto">
    <Icon name="close-outline" class="z-10 absolute mt-[11.5%] left-[47.5%] w-[8%] h-[8%] text-orange-200" />
    <div class="absolute w-[60%] mt-[20.5%] ml-[21%] flex flex-col">
        <p class="font-lickorishe text-[4vw]/[5vw] lg:text-[3.5vh]/[4.96vh] text-orange-600 select-none relative text-left">5. We do not do piercings at this time.</p>
    </div>
    <img src={smallAnswer} alt="small answer background" class="w-[100%] max-w-none max-h-none">
</button>

<button on:click={() => change(0)} class="{selected == 6 ? "" : "hidden"} absolute left-[0%] top-[30%] w-fit lg:left-[25%] lg:top-[20%] lg:w-[100vh] h-auto">
    <Icon name="close-outline" class="z-10 absolute mt-[11.5%] left-[47.5%] w-[8%] h-[8%] text-orange-200" />
    <div class="absolute w-[60%] mt-[20.5%] ml-[21%] flex flex-col">
        <p class="font-lickorishe text-[4vw]/[5vw] lg:text-[3.5vh]/[4.96vh] text-orange-600 select-none relative text-left">6. We do not tattoo minors.</p>
    </div>
    <img src={smallAnswer} alt="small answer background" class="w-[100%] max-w-none max-h-none">
</button>

<button on:click={() => change(0)} class="{selected == 7 ? "" : "hidden"} absolute left-[0%] top-[30%] w-fit lg:left-[25%] lg:top-[20%] lg:w-[100vh] h-auto">
    <Icon name="close-outline" class="z-10 absolute mt-[11.5%] left-[47.5%] w-[8%] h-[8%] text-orange-200" />
    <div class="absolute w-[60%] mt-[20.5%] ml-[21%] flex flex-col">
        <p class="font-lickorishe text-[4vw]/[5vw] lg:text-[3.5vh]/[4.96vh] text-orange-600 select-none relative text-left">7. See instructions below for our studio process.</p>
    </div>
    <Button href="https://drive.google.com/file/d/1gYpqS_WbpQNxplEW4eaDrpHODULh9u9m/view?usp=sharing" target="_blank" color="red" type="submit" class="text-[5vw]/[3.8vw] lg:text-[4.2vh]/[3.8vh] absolute left-[36%] top-[64%] w-[30%] h-[15%]">Attachment</Button>
    <img src={smallAnswer} alt="small answer background" class="w-[100%] max-w-none max-h-none">
</button>

<button on:click={() => change(0)} class="{selected == 8 ? "" : "hidden"} absolute left-[0%] top-[15%] w-fit lg:left-[25%] lg:top-[0%] lg:w-[100vh] h-auto">
    <Icon name="close-outline" class="z-10 absolute mt-[10%] left-[47.5%] w-[5%] h-[5%] text-orange-200" />
    <div class="absolute w-[61%] mt-[19.3%] ml-[21%] flex flex-col">
        <p class="font-lickorishe text-[3.4vw]/[4.8vw] lg:text-[3.4vh]/[4.8vh] text-orange-600 select-none relative text-left">8. We are not medical professionals and advise consulting with one if you have any concerns about getting a tattoo. If your provider has greenlit the procedure, we are happy to provide accommodations that may help you have a more comfortable and safe experience. If your concerns are allergy related, you are welcome to look through the ingredients of our products or, depending on the product, provide a sample for you to test on your skin.</p>
    </div>
    <img src={bigAnswer} alt="big answer background" class="w-[100%] max-w-none max-h-none">
</button>
