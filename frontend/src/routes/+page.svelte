<script>
    // import horinzontalLoop from "$lib/horizontalLoop.js"
    import {onMount} from "svelte";
    import {gsap} from "gsap";
    import {ScrollTrigger} from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger)
    onMount(() => {
        document.title = "Andrey Li"

        const images = gsap.utils.toArray(".card-image")

        images.forEach(image => {
            gsap.set(image, {
                scale: 1.14,
                yPercent: 7
            })

            gsap.to(image, {
                yPercent: -7,
                scrollTrigger: {
                    trigger: image.parentElement.parentElement, // the corresponding .card
                    start: "top bottom",
                    end: "bottom top",
                    scrub: true,
                    markers: true
                }
            })
        })
    })
</script>

<section class="w-full bg-stone-100">
    <header class="fixed h-[10%] bg-stone-100/40 backdrop-blur-sm p-4 text-3xl z-30 w-full shadow-lg flex items-center justify-between">
        <div>
            <span class="text-soundblue">Andrey</span><span class="text-soundred">Li</span>.com
        </div>
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.2"><path d="M3 12a9 9 0 1 0 18 0a9 9 0 0 0-18 0m.6-3h16.8M3.6 15h16.8"/><path d="M11.5 3a17 17 0 0 0 0 18m1-18a17 17 0 0 1 0 18"/></g></svg>
    </header>

    <div class="card w-full h-screen relative container">
        <div class="w-full h-[65%] absolute left-0 top-[10%] overflow-hidden">
            <img class="card-image w-full h-full object-cover aspect-[3/4]" src="/photos/onField7.png" alt="">
        </div>
        <div class="w-full h-[25%] absolute bottom-0 p-4">
            <div class="text-3xl flex items-center justify-between">
                <h1 class="text-stone-800">
                    Topic
                </h1>
                <h2 class="text-xl text-stone-600">
                    date
                </h2>
            </div>
            <p class="text-xl text-stone-600 mt-2">
                Multiline description about the athlete, about a paragraph long.
            </p>
        </div>
    </div>

    <div class="card w-full h-screen relative container">
        <div class="w-full h-[65%] absolute left-0 top-[10%] overflow-hidden">
            <img class="card-image w-full h-full object-cover aspect-[3/4]" src="/photos/skillsInstitute.JPEG" alt="">
        </div>
        <div class="w-full h-[25%] absolute bottom-0 p-4">
            <div class="text-3xl flex items-center justify-between">
                <h1 class="text-stone-800">
                    Topic
                </h1>
                <h2 class="text-xl text-stone-600">
                    date
                </h2>
            </div>
            <p class="text-xl text-stone-600 mt-2">
                Multiline description about the athlete, about a paragraph long.
            </p>
        </div>
    </div>

    <div class="card w-full h-screen relative container">
        <div class="w-full h-[65%] absolute left-0 top-[10%] overflow-hidden">
            <img class="card-image w-full h-full object-cover aspect-[3/4]" src="/photos/withCoach4.png" alt="">
        </div>
        <div class="w-full h-[25%] absolute bottom-0 p-4">
            <div class="text-3xl flex items-center justify-between">
                <h1 class="text-stone-800">
                    Topic
                </h1>
                <h2 class="text-xl text-stone-600">
                    date
                </h2>
            </div>
            <p class="text-xl text-stone-600 mt-2">
                Multiline description about the athlete, about a paragraph long.
            </p>
        </div>
    </div>
    
</section>