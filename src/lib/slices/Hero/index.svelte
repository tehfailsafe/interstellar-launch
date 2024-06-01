<script lang="ts">
	import Button from '$lib/components/Button.svelte';
	import { PrismicImage, PrismicRichText, PrismicText } from '@prismicio/svelte';
	import type { Content } from '@prismicio/client';

	export let slice: Content.HeroSlice;
</script>

<section class="py-12 md:py-24">
	<div
		class={`@container flex flex-col gap-12 md:flex-row md:items-center ${slice.primary.reversed ? 'flex-row-reverse' : ''} ${slice.variation === 'default' ? 'container' : 'max-w-3xl text-center mx-auto text-on-primary justify-center items-center'}`}
	>
		<div class="flex flex-col flex-1 gap-4 md:gap-6">
			<!-- <PrismicRichText class="" field={slice.primary.header} /> -->
			<h1 class="">
				{slice.primary.header[0]?.text}
			</h1>
			<PrismicRichText field={slice.primary.body} />

			{#if slice.primary.input_action}
				<form
					action={slice.primary.input_action}
					method="POST"
					class="flex gap-4 mt-4"
					autocomplete="off"
					{...$$restProps}
				>
					<input
						type="email"
						name="email"
						placeholder={slice.primary.input_placeholder}
						class="input"
					/>
					<Button type="submit">{slice.primary.input_cta}</Button>
				</form>
			{:else if slice.primary.actions.length > 0}
				<div class="flex gap-4">
					{#each slice.primary.actions as item}
						<Button field={item.link} variant={item.variant}>{item.title}</Button>
					{/each}
				</div>
			{/if}
		</div>
		{#if slice.variation === 'default'}
			<div class="flex-1">
				{#if slice.primary.bg_image}
					<PrismicImage class="object-cover w-full aspect-square" field={slice.primary.bg_image} />
				{/if}
			</div>
		{/if}
	</div>

	{#if slice.variation === 'fullBackgroundImage'}
		<div class="absolute inset-0 -z-10">
			<PrismicImage field={slice.primary.bg_image} class="object-cover size-full" />
			<div class="absolute inset-0 bg-black/50"></div>
		</div>
	{/if}

	<!-- <div
			class="absolute inset-0 bg-cover bg-center top-0 left-0 bottom-0 right-0 -z-10 bg-black/80"
		>
			<div class="w-full h-full z-10 bg-red-500/50" />
		</div> -->
</section>
