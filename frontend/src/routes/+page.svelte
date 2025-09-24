<script>
    // import horinzontalLoop from "$lib/horizontalLoop.js"
    import {onMount} from "svelte";
    import {gsap} from "gsap";
    import {ScrollTrigger} from "gsap/ScrollTrigger";

    let landingPhoto
    let miniPhotoSection

    gsap.registerPlugin(ScrollTrigger)
    onMount(() => {
        document.title = "Andrey Li"

        gsap.set(landingPhoto, {
            "--t": 0,
            "--r": 0,
            "--b": 0,
            "--l": 0
        })

        const scaleFraction = 10 // scale down by x%

        gsap.to(landingPhoto, {
            "--t": `${scaleFraction}%`,
            "--r": `${scaleFraction}%`,
            "--b": "20%", // hardcoded because its not important for positioning
            "--l": `${scaleFraction}%`,
            scale: (100 - scaleFraction) / 100,
            y: innerHeight - landingPhoto.height * Math.pow(scaleFraction / 100, 2) - landingPhoto.width * (scaleFraction / 100),
            scrollTrigger: {
                trigger: miniPhotoSection,
                start: "top bottom",
                end: "bottom bottom",
                scrub: true,
            },
            ease: "none"
        })
    })
</script>

<header class="fixed h-[10%] bg-stone-100/40 backdrop-blur-sm p-4 text-3xl z-30 w-full shadow-lg flex items-center justify-between">
    <div>
        <span class="text-sblue">Andrey&nbsp;</span><span class="text-sred">Li</span>
    </div>
    <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.2"><path d="M3 12a9 9 0 1 0 18 0a9 9 0 0 0-18 0m.6-3h16.8M3.6 15h16.8"/><path d="M11.5 3a17 17 0 0 0 0 18m1-18a17 17 0 0 1 0 18"/></g></svg>
</header>

<section class="relative w-full h-screen bg-stone-100">
    <img bind:this={landingPhoto} src="/photos/onField7.png" alt="" class="absolute top-[10%] w-screen h-[90vh] object-cover z-10" style="clip-path: inset(var(--t) var(--r) var(--b) var(--l))">
</section>

<section bind:this={miniPhotoSection} class="relative w-full h-screen bg-stone-100">
    <div class="absolute w-full h-[25%] p-4 bottom-0 left-0 flex flex-col">
        <h1 class="text-4xl text-sblue font-semibold">Andrey Li</h1>
        <p class="text-stone-600 text-2xl mt-2">
            Introduction about the athlete, about a paragraph long.
        </p>
    </div>
</section>

<section class="relative w-full h-screen bg-stone-100">
    <div class="absolute w-full h-[90%] top-[10%] flex items-center justify-center space-x-12 p-6">

        <div class="card relative border-8 border-sblue w-full h-full">
            <div class="absolute left-0 bottom-0 w-full h-fit z-20 p-4">
                <h1 class="text-2xl text-sblue">
                    <span class="font-semibold">
                        2025, June
                    </span>
                    Title
                </h1>
                <p class="text-xl text-sblue-muted mt-2">
                    Introduction about the athlete, about a paragraph long.
                </p>
            </div>
            <div class="absolute left-0 top-0 w-full h-full z-10 bg-gradient-to-t from-black to-transparent to-80%"></div>
            <img src="/photos/onField1.png" alt="" class="object-cover w-full h-full">
        </div>

    </div>
</section>