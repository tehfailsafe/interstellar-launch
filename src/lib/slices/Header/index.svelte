<script>
	import Button from '$lib/components/Button.svelte';
	import { PrismicLink } from '@prismicio/svelte';

	/** @type {import("@prismicio/client").Content.HeaderSlice} */
	export let slice;
</script>

<header class="">
	<div class="container flex items-center justify-between py-6">
		<PrismicLink field={slice.primary.logo}>Logo</PrismicLink>
		<div class="flex items-center gap-4">
			{#each slice.primary.links as item}
				{#if item.button}
					<Button field={item.link} variant={item.button_variant}>{item.text}</Button>
				{:else}
					<PrismicLink field={item.link}>{item.text}</PrismicLink>
				{/if}
			{/each}
		</div>
	</div>
</header>
