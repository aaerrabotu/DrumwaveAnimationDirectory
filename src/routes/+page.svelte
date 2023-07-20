<script lang="ts">
	import logo from './logo.png';
	import blendedHexThumb from './blended-hex/thumb.png';
	import strokeWidthThumb from './stroke-width/thumb.png';
	import overlappingColorThumb from './overlapping-color/thumb.png';
	import overlappingRedThumb from './overlapping-red/thumb.png';
	import partsColorThumb from './parts-color/thumb.png';
	import partsRedThumb from './parts-red/thumb.png';
</script>

<svelte:head>
	<title>DrumWave - Dynamic Logo Explorations</title>
</svelte:head>

<article>
	<header>
		<figure>
			<img src={logo} alt="DrumWave Logo" />
		</figure>
		<h1>DrumWave</h1>
	</header>

	<h2>Dynamic Logo Explorations</h2>

	<nav>
		<a href="stroke-width">
			<img src={strokeWidthThumb} alt="Stroke Width Animation Thumbnail" />
			<span>Stroke Width Animation</span>
		</a>
		<a href="overlapping-color">
			<img src={overlappingColorThumb} alt="Overlapping 7 Section Animation (Colored) Thumbnail" />
			<span>Overlapping 7 Section Animation (Colored)</span>
		</a>
		<a href="parts-red">
			<img src={partsRedThumb} alt="7 Drumwave Parts Animation (Red) Thumbnail" />
			<span>7 Drumwave Parts Animation (Red)</span>
		</a>
		<a href="overlapping-red">
			<img src={overlappingRedThumb} alt="Overlapping 7 Section Animation (Red) Thumbnail" />
			<span>Overlapping 7 Section Animation (Red)</span>
		</a>
		<a href="parts-color">
			<img src={partsColorThumb} alt="7 Drumwave Parts Animation (Parts Only) Thumbnail" />
			<span>7 Drumwave Parts Animation (Parts Only)</span>
		</a>
		<a href="blended-hex">
			<img src={blendedHexThumb} alt="Blended Colors Using HEX Values! Thumbnail" />
			<span>Blended Colors Using HEX Values!</span>
		</a>
	</nav>
</article>

<style>
	article {
		max-width: 800px;
		margin: 0 auto;
		padding: 40px;
		background-color: #fff;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	}

	header {
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 20px;
	}

	figure {
		all: unset;
		width: 50px;
		height: 50px;
		margin-right: 10px;
	}

	figure img {
		max-width: 100%;
		max-height: 100%;
	}

	h1 {
		margin: 0;
		font-size: 48px;
		font-weight: bold;
		color: #333;
		text-align: center;
	}

	h2 {
		margin-top: 20px;
		font-size: 24px;
		font-weight: bold;
		color: #555;
		text-align: center;
	}

	nav {
		align-items: flex-start;
		display: flex;
		flex-direction: column;
		gap: 10px;
		margin: 20px auto;
		width: max-content;
	}

	nav a {
		align-items: center;
		border-radius: 4px;
		color: inherit;
		display: inline-flex;
		text-decoration: none;
	}

	nav a:hover {
		background-color: hsl(0, 0%, 95%);
	}

	nav img {
		height: 50px;
		mix-blend-mode: multiply;
		width: 50px;
	}

	nav span {
		padding: 10px;
	}
</style>
