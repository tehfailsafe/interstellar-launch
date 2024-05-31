<script>
	import { PrismicPreview } from '@prismicio/svelte/kit';
	import { page } from '$app/stores';
	import { repositoryName } from '$lib/prismicio';
	import '../app.css';
</script>

<svelte:head>
	<title>{$page.data.title}</title>
	<meta name="color-scheme" content="light only" />
	{#if $page.data.meta_description}
		<meta name="description" content={$page.data.meta_description} />
	{/if}
	{#if $page.data.meta_title}
		<meta name="og:title" content={$page.data.meta_title} />
	{/if}
	{#if $page.data.meta_image}
		<meta name="og:image" content={$page.data.meta_image} />
		<meta name="twitter:card" content="summary_large_image" />
	{/if}
	<script
		async
		defer
		src="https://static.cdn.prismic.io/prismic.js?new=true&repo=prismic-starter-base"
	></script>
</svelte:head>
<main class="bg-surface">
	<slot />
</main>
<PrismicPreview {repositoryName} />
