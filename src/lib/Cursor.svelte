<script>
	import { onMount } from 'svelte';
	let cursor;
	onMount(() => {
		document.addEventListener('mousemove', (e) => {
			cursor.style.transform = `translate(${e.clientX}px, ${e.clientY}px)`;
			// make the cursor follow the mouse with pinpoint accuracy

			cursor.style.transform = `translate(${e.clientX - 8}px, ${e.clientY - 8}px)`; // 8 is half the width and height of the cursor
		});
	});
</script>

<div
	class="cursor w-8 h-8 bg-white rounded-full z-[999] mix-blend-difference fixed"
	bind:this={cursor}
/>

<style>
	.cursor {
		position: fixed;
		top: 0;
		left: 0;
		transform: translate(-50%, -50%);
		pointer-events: none;
	}
</style>
