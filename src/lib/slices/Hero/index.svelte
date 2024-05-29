<script>
	import Button from '$lib/components/Button.svelte';
	import { PrismicImage, PrismicRichText } from '@prismicio/svelte';

	/** @type {import("@prismicio/client").Content.HeroSlice} */
	export let slice;
	console.log(slice.primary.body);
</script>

<section class="relative flex text-center justify-center items-center px-8 py-20 w-full text-white">
	<div class="flex flex-col items-center my-16 md:my-32 max-w-prose gap-4 container">
		<h1>
			{slice.primary.header}
		</h1>

		<div class="mb-12">
			<PrismicRichText field={slice.primary.body} />
		</div>

		<div class="flex gap-4 text-sm">
			{#each slice.primary.actions as item}
				<Button field={item.link} variant={item.variant}>{item.title}</Button>
			{/each}
		</div>
	</div>
	<div class="absolute w-full h-full top-0 left-0 -z-10">
		<PrismicImage field={slice.primary.bg_image} class="object-cover size-full" />
		<div class="absolute inset-0 bg-primary-500/80" />
	</div>
</section>
