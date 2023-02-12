<script>
	import 'sticksy';
	import circleType from 'circletype';
	import { onMount } from 'svelte';
	var felaText;

	onMount(() => {
		var stickyFelaImage = new Sticksy('.fela-sticky', { topSpacing: window.innerHeight / 2 - 100 });
		stickyFelaImage.onStateChanged = function (state) {
			if (state === 'fixed') {
				stickyFelaImage.nodeRef.classList.add('widget--sticky');
			} else {
				stickyFelaImage.nodeRef.classList.remove('widget--sticky');
			}
		};

		new circleType(felaText);
		document.addEventListener('scroll', () => {
			felaText.style.transform = `rotate(${window.scrollY / 10}deg)`;
		});
	});
</script>

<div class="h-fit w-screen flex py-8">
	<!-- create two divs side by side of equal size -->
	<div class="w-1/3">
		<div class="fela-sticky">
			<div class="h-full w-full flex justify-center items-center">
				<img
					src="hg3qi2j77zgyh1vjzgjr-removebg-preview.png"
					class="w-fit h-fit object-cover object-center z-10"
					alt=""
				/>
				<div
					class="fela-sticky-round-text absolute text-[2rem] font-medium"
					id="sticky-image"
					bind:this={felaText}
				>
					Fela Anikulapo-Kuti Fela Anikulapo-Kuti Fela Anikulapo-Kuti
				</div>
			</div>
		</div>
	</div>
	<div class="w-2/3 text-[3rem] font-medium px-6">
		<p>
			Fela Anikulapo Kuti (1938-1997) was a Nigerian musician, composer, and human rights activist.
			He is considered one of the most influential figures in African music and a pioneer of the
			Afrobeat genre, which blends traditional West African music with funk and jazz.
		</p>
		<p>
			Fela's music often dealt with political and social issues, such as government corruption and
			oppression. He used his music as a platform to raise awareness and bring about change, and his
			lyrics and stage performances were often seen as controversial and subversive.
		</p>
		<p>
			Fela was a fearless critic of the Nigerian government and he wasn't afraid to use his music to
			speak out against corruption and injustice. This often led to conflict with the authorities
			and resulted in Fela spending time in prison. Despite these challenges, he continued to
			produce music that inspired and empowered people, and he remained an important figure in the
			fight for human rights in Nigeria and beyond.
		</p>
	</div>
</div>
