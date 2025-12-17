<script>
    import { gsap } from "gsap";
    import { Draggable } from "gsap/Draggable";
    import { InertiaPlugin } from "gsap/InertiaPlugin";
    import { onMount } from "svelte";
    import horizontalLoop from "$lib/horizontalLoop";

    gsap.registerPlugin(Draggable);
    gsap.registerPlugin(InertiaPlugin);

    let { cards, id, photosOnly = false } = $props();

    onMount(() => {
        let activeElement;
        const cards = gsap.utils.toArray(`#${id}`);
        const loop = horizontalLoop(cards, {
            paused: true,
            draggable: true,
            center: true,
            onChange: (element, index) => {
                activeElement && activeElement.classList.remove("active");
                element.classList.add("active");
                activeElement = element;
            },
        });
    });
</script>

{#each cards as card}
    <div
        class="relative shadow-lg shadow-black/25 w-full h-full flex flex-col flex-shrink-0"
        {id}
    >
        {#if !photosOnly}
            <img src={card.src} alt="" class="object-cover h-[60%]" />
            <div class="p-4 flex-1">
                <h1 class="text-3xl text-sblue font-semibold">{card.title}</h1>
                <h2 class="text-2xl text-sblue-muted">{card.date}</h2>
                <p class="text-2xl text-stone-600 mt-2">
                    {card.description}
                </p>
            </div>
        {:else}
            <img src={card.src} alt="" class="object-cover w-full h-full" />
        {/if}
    </div>
{/each}
