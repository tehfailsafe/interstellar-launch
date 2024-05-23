<script>
	import { PrismicRichText } from '@prismicio/svelte';

	/** @type {import("@prismicio/client").Content.HeroSlice} */
	export let slice;
</script>

<section data-slice-type={slice.slice_type} data-slice-variation={slice.variation}>
	<div>
		<h1>{slice.primary.header}</h1>
		<p><PrismicRichText field={slice.primary.body} /></p>
	</div>
</section>

<style>
	section {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
		width: 100%;
		background-color: black;
		background-image: url({slice.primary.bg_image.url});
		background-size: cover;
		background-position: center;

		--slice-color: #ffaa00;
	}
	div {
		display: flex;
		flex-direction: column;
	}

	h1 {
		color: white;
		text-align: center;
		font-size: 5em;
		font-weight: bold;
		text-transform: uppercase;
		max-width: 65ch;
	}

	p {
		color: white;
	}
</style>
