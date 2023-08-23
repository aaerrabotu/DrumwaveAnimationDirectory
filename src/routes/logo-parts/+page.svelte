<script lang="ts">
	import { onMount } from 'svelte';

	import one from './one.svg';
	import two from './two.svg';
	import three from './three.svg';
	import four from './four.svg';
	import five from './five.svg';
	import six from './six.svg';
	import seven from './seven.svg';

	let imageContainer: HTMLElement;

	onMount(function () {
		let images = imageContainer.getElementsByTagName('img');
		let currentIndex = 0;
		let totalImages = images.length;
		let direction = 1; // 1 for forward, -1 for reverse
		let timeout: ReturnType<typeof setTimeout>;

		function showNextImage() {
			let previousIndex = currentIndex;
			currentIndex += direction;

			if (currentIndex >= totalImages) {
				currentIndex = totalImages - 2;
				direction = -1;
			} else if (currentIndex < 0) {
				currentIndex = 1;
				direction = 1;
			}

			images[previousIndex].style.opacity = '0.5'; // Set the opacity of the previous image to 0.5
			images[currentIndex].style.opacity = '0.5'; // Set the opacity of the current image to 0.5

			timeout = setTimeout(function () {
				images[previousIndex].style.opacity = '0'; // Fade out the previous image completely
				images[currentIndex].style.opacity = '1'; // Fade in the current image
				timeout = setTimeout(function () {
					images[previousIndex].style.opacity = '0'; // Reset the previous image's opacity to 0
				}, 1000); // Adjust the time (milliseconds) to reset the previous image
			}, 1000); // Adjust the time (milliseconds) to blend the images
		}

		let interval = setInterval(showNextImage, 4000); // Change image every 4 seconds (slower transition)

		return function () {
			clearInterval(interval);
			clearTimeout(timeout);
		};
	});
</script>

<svelte:head>
	<title>Logo Parts</title>
</svelte:head>

<div bind:this={imageContainer} class="image-container">
	<img src={one} alt="First segment" style="opacity: 1;" />
	<img src={two} alt="Second segment" />
	<img src={three} alt="Third segment" />
	<img src={four} alt="Fourth segment" />
	<img src={five} alt="Fifth segment" />
	<img src={six} alt="Sixth segment" />
	<img src={seven} alt="Seventh segment" />
</div>

<style>
	.image-container {
		position: relative;
		width: 715px;
		height: 715px;
	}

	.image-container img {
		position: absolute;
		top: 0;
		left: 0;
		opacity: 0;
		transition: opacity 2s ease-in-out; /* Adjust the transition time as desired */
		width: 750px; /* Adjust the width value as desired */
		height: 750px; /* Adjust the height value as desired */
	}
</style>
