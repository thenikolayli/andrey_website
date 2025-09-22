<script>
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import {onMount} from "svelte";
	import {gsap} from "gsap";
	import {ScrollTrigger} from "gsap/ScrollTrigger";
	import Lenis from "lenis";
	
	let { children } = $props();

	onMount(() => {
		const lenis = new Lenis()
		lenis.on("scroll", ScrollTrigger.update)
		gsap.ticker.add((time) => {
			lenis.raf(time * 1000)
		})
		gsap.ticker.lagSmoothing(0)
	})
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children?.()}
