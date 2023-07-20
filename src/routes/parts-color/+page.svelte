<script lang="ts">
	import { onMount } from 'svelte';
	import segment1 from './1.png';
	import segment2 from './2.png';
	import segment3 from './3.png';
	import segment4 from './4.png';
	import segment5 from './5.png';
	import segment6 from './6.png';
	import segment7 from './7.png';

	let container: HTMLElement;

	onMount(function () {
		const images = container.querySelectorAll('img');
		const totalImages = images.length;
		let currentIndex = 0;

		function showNextImage() {
			const previousIndex = currentIndex;
			currentIndex = (currentIndex + 1) % totalImages;
			images[previousIndex].style.opacity = '0';
			images[currentIndex].style.opacity = '1';
		}

		showNextImage();
		const id = setInterval(showNextImage, 2000);

		return function () {
			clearInterval(id);
		};
	});
</script>

<figure bind:this={container}>
	<img src={segment5} alt="Segment 5" />
	<img src={segment1} alt="Segment 1" />
	<img src={segment4} alt="Segment 4" />
	<img src={segment7} alt="Segment 7" />
	<img src={segment2} alt="Segment 2" />
	<img src={segment3} alt="Segment 3" />
	<img src={segment6} alt="Segment 6" />
</figure>

<style>
	figure {
		all: unset;
		display: block;
		position: relative;
		width: 500px;
		height: 500px;
	}

	img {
		position: absolute;
		top: 0;
		left: 0;
		opacity: 0;
		transition: opacity 0.5s ease-in-out;
		width: 100%;
		height: 100%;
	}
</style>
