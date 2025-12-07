<script>
    import horizontalLoop from "$lib/horizontalLoop.js";
    import { onMount } from "svelte";
    import { gsap } from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { Draggable } from "gsap/Draggable";
    import { InertiaPlugin } from "gsap/InertiaPlugin";
    import Carousel from "$lib/components/carousel.svelte";

    let landingPhoto;
    let miniPhotoSection;
    const cards = [
        {
            date: "June, 2025",
            title: "Some Game",
            description: "small paragraph",
            src: "/photos/inCar.JPEG",
        },
        {
            date: "June, 2025",
            title: "Some Game",
            description: "small paragraph",
            src: "/photos/onField1.png",
        },
    ];

    gsap.registerPlugin(ScrollTrigger);
    gsap.registerPlugin(Draggable);
    gsap.registerPlugin(InertiaPlugin);
    onMount(() => {
        document.title = "Andrey Li";

        gsap.set(landingPhoto, {
            "--t": 0,
            "--r": 0,
            "--b": 0,
            "--l": 0,
        });

        const scaleFraction = 10; // scale down by x%

        gsap.to(landingPhoto, {
            "--t": `${scaleFraction * 2}%`,
            "--r": `${scaleFraction}%`,
            "--b": "20%", // hardcoded because its not important for positioning
            "--l": `${scaleFraction}%`,
            scale: (100 - scaleFraction) / 100,
            y:
                innerHeight -
                landingPhoto.height * Math.pow(scaleFraction / 100, 2) -
                landingPhoto.width * (scaleFraction / 100),
            scrollTrigger: {
                trigger: miniPhotoSection,
                start: "top bottom",
                end: "bottom bottom",
                scrub: true,
            },
            ease: "none",
        });
    });
</script>

<header
    class="fixed h-[6vh] bg-stone-100/40 backdrop-blur-sm p-8 text-3xl z-30 w-full shadow-lg flex items-center justify-between"
>
    <div>
        <span class="text-sblue">Andrey&nbsp;</span><span class="text-sred"
            >Li</span
        >
    </div>
    <svg
        xmlns="http://www.w3.org/2000/svg"
        width="1em"
        height="1em"
        viewBox="0 0 24 24"
        ><g
            fill="none"
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="1.2"
            ><path
                d="M3 12a9 9 0 1 0 18 0a9 9 0 0 0-18 0m.6-3h16.8M3.6 15h16.8"
            /><path d="M11.5 3a17 17 0 0 0 0 18m1-18a17 17 0 0 1 0 18" /></g
        ></svg
    >
</header>

<section class="relative w-full h-screen bg-stone-100">
    <img
        bind:this={landingPhoto}
        src="/photos/onField7.png"
        alt=""
        class="absolute pt-[6vh] w-screen h-full object-cover z-10"
        style="clip-path: inset(var(--t) var(--r) var(--b) var(--l))"
    />
</section>

<section
    bind:this={miniPhotoSection}
    class="relative w-full h-screen bg-stone-100"
>
    <div
        class="absolute w-full h-[25vh] py-4 px-8 bottom-0 left-0 flex flex-col"
    >
        <h1 class="text-4xl text-sblue font-semibold">Andrey Li</h1>
        <p class="text-stone-600 text-2xl mt-2">
            Introduction about the athlete, about a paragraph long.
        </p>
    </div>
</section>

<section
    class="relative w-full h-screen bg-stone-100 pt-[6vh] px-0 flex flex-col items-center justify-center"
>
    <header class="w-full font-semibold text-sblue text-4xl px-8 py-4">
        Highlights
    </header>
    <div
        class="relative w-full flex-1 flex items-center justify-start overflow-hidden pb-8 px-8 space-x-8"
    >
        <Carousel {cards} />
    </div>
</section>

<section
    class="relative w-full h-screen bg-stone-100 pt-[6vh] flex flex-col items-center justify-center p-8"
>
    <img class="object-contain" src="/photos/withTrophy2.png" alt="" />
    <h1 class="text-3xl text-sblue text-center font-semibold mt-2">
        Follow my Instagram!
    </h1>
    <a
        target="_blank"
        href="https://instagram.com/theandreyli"
        class="relative mx-auto w-fit h-fit mt-4 p-4 flex items-center justify-center"
    >
        <svg
            class="relative z-10 w-[3em] h-[3em] mr-2"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            ><path
                fill="var(--color-stone-200)"
                d="M7.8 2h8.4C19.4 2 22 4.6 22 7.8v8.4a5.8 5.8 0 0 1-5.8 5.8H7.8C4.6 22 2 19.4 2 16.2V7.8A5.8 5.8 0 0 1 7.8 2m-.2 2A3.6 3.6 0 0 0 4 7.6v8.8C4 18.39 5.61 20 7.6 20h8.8a3.6 3.6 0 0 0 3.6-3.6V7.6C20 5.61 18.39 4 16.4 4zm9.65 1.5a1.25 1.25 0 0 1 1.25 1.25A1.25 1.25 0 0 1 17.25 8A1.25 1.25 0 0 1 16 6.75a1.25 1.25 0 0 1 1.25-1.25M12 7a5 5 0 0 1 5 5a5 5 0 0 1-5 5a5 5 0 0 1-5-5a5 5 0 0 1 5-5m0 2a3 3 0 0 0-3 3a3 3 0 0 0 3 3a3 3 0 0 0 3-3a3 3 0 0 0-3-3"
            /></svg
        >
        <h1 class="relative z-10 text-2xl text-stone-200">@theandreyli</h1>
        <img
            src="/Instagram_Gradient.png"
            alt=""
            class="absolute w-full h-full object-cover left-0 top-0"
        />
    </a>
</section>
