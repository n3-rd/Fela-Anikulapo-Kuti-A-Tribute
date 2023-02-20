<script>
	import 'sticksy';
	import { onMount } from 'svelte';
	import ArrowDiagonalDown from './ArrowDiagonalDown.svelte';
	let music = [];
	let musicItems;
	const fetchMusic = async () => {
		const response = await fetch(
			'https://rich-cyan-sturgeon-sock.cyclic.app/getArtistTracks?artistId=5CG9X521RDFWCuAhlo6QoR'
		);
		const data = await response.json();
		music = data.tracks;
	};

	const switchImage = () => {
		const musicItems = document.querySelectorAll('.music-item');
		console.log(musicItems);
		musicItems.forEach((item) => {
			item.addEventListener('mouseEnter', () => {
				const musicImage = document.querySelector('.music-image');
				musicImage.src = item.dataset.musicImage;
				// refresh the Image
				musicImage.src = musicImage.src;
			});
		});
	};

	onMount(() => {
		var stickyMusicImage = new Sticksy('.music-sticky', {
			listen: true,
			topSpacing: window.innerHeight / 2 - 100
		});
		stickyMusicImage.onStateChanged = function (state) {
			if (state === 'fixed') {
				stickyMusicImage.nodeRef.classList.add('widget--sticky');
			} else {
				stickyMusicImage.nodeRef.classList.remove('widget--sticky');
			}
		};
		fetchMusic();
	});
</script>

<div class="h3 font-black text-[4rem] uppercase mt-24 py-4">Top Music by Fela</div>
<div class="music w-screen h-fit flex" id="music">
	<div class="w-2/3">
		{#each music as song}
			<a href={song.external_urls.spotify} target="_blank" rel="noreferrer">
				<div
					class="music-item border-b-2 border-white text-[3rem] font-black px-2 flex"
					data-music-image={song.album.images[0].url}
				>
					<div class="w-10/12 flex items-center">
						{song.name}
					</div>
					<div class="w-2/12">
						<ArrowDiagonalDown />
					</div>
				</div>
			</a>
		{/each}
	</div>
	<div class="w-1/3">
		<div class="music-sticky">
			<div class="h-full w-full flex justify-center items-center">
				<img
					src="/3680.jpg"
					class="w-fit h-fit object-cover object-center z-10 music-image"
					alt=""
				/>
			</div>
		</div>
	</div>
</div>
