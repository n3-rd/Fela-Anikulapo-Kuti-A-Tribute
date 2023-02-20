<script>
	import ArrowDiagonal from './ArrowDiagonal.svelte';
	import luge from '@waaark/luge';
	import { onDestroy, onMount } from 'svelte';

	// onDestroy(() => {
	// 	luge.lifecycle.refresh();
	// });

	onMount(() => {
		const sepiaSection = document.querySelector('.sepia-section');
		luge.scrollobserver.add(sepiaSection);

		sepiaSection.addEventListener('scrollprogress', (e) => {
			e.target.style.filter = `grayscale(${e.target.scrollProgress})`;
		});
	});
</script>

<div class="hero h-screen w-screen flex flex-col justify-center items-end bg-black">
	<div
		class="large font-black text-[8vw] text-center h-[30vh] w-full [word-spacing:1.2875rem
    ] text-white"
	>
		FELA ANIKULAPO-KUTI
	</div>
	<div class="w-full h-[70vh] flex items-end justify-end">
		<div
			class="w-[30vw] h-full flex flex-col justify-center items-center links font-bold uppercase text-white text-[3rem]"
		>
			<a href="#about" class="flex items-center cursor-pointer">About <ArrowDiagonal /></a>
			<a href="#music" class="flex items-center cursor-pointer ">Music <ArrowDiagonal /></a>
		</div>
		<!-- <Saos animation={'grayscale 4s linear '}> -->
		<div class="hero-images w-[70vw] h-full flex justify-center items-center sepia-section ">
			<div class="bg-center bg-cover bg-[url(/ptbbrhvazypworkpvxfb.jpg)] w-1/2 h-full" />
			<div class="bg-center bg-cover bg-[url(/3680.jpg)] w-1/2 h-full" />
		</div>
		<!-- </Saos> -->
	</div>
</div>

<style>
	@keyframes -global-grayscale {
		0% {
			filter: grayscale(0);
		}
		100% {
			filter: grayscale(1);
		}
	}
</style>
