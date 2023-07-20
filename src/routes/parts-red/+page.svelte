<script lang="ts">
	import { onMount } from 'svelte';
	import segment1 from './1.svg';
	import segment2 from './2.svg';
	import segment3 from './3.svg';
	import segment4 from './4.svg';
	import segment5 from './5.svg';
	import segment6 from './6.svg';
	import segment7 from './7.svg';

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
	<img src={segment1} alt="Segment 1" />
	<img src={segment3} alt="Segment 2" />
	<img src={segment2} alt="Segment 3" />
	<img src={segment4} alt="Segment 4" />
	<img src={segment5} alt="Segment 5" />
	<img src={segment6} alt="Segment 6" />
	<img src={segment7} alt="Segment 7" />
</figure>

<style>
	figure {
		all: unset;
		position: relative;
		width: 715px;
		height: 715px;
	}

	img {
		position: absolute;
		top: 0;
		left: 0;
		opacity: 0;
		transition: opacity 0.5s ease-in-out;
		width: 750px; /* Adjust the width value as desired */
		height: 750px; /* Adjust the height value as desired */
	}
</style>
