<script>
	import Hero from '../lib/Hero.svelte';
	import Lenis from '@studio-freight/lenis';
	import { onMount } from 'svelte';
	import About from '../lib/About.svelte';
	import Cursor from '../lib/Cursor.svelte';
	import Videos from '../lib/Videos.svelte';
	import Music from '../lib/Music.svelte';

	const smoothScroll = () => {
		const lenis = new Lenis({
			duration: 2.2,
			easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)), // https://www.desmos.com/calculator/brs54l4xou
			direction: 'vertical', // vertical, horizontal
			gestureDirection: 'vertical', // vertical, horizontal, both
			smooth: true,
			mouseMultiplier: 2,
			smoothTouch: false,
			touchMultiplier: 2,
			infinite: false
		});

		function raf(time) {
			lenis.raf(time);
			requestAnimationFrame(raf);
		}

		requestAnimationFrame(raf);
	};

	onMount(() => {
		smoothScroll();
	});
</script>

<Cursor />
<Hero />
<About />
<Music />

<div class="h-screen" />
