<script>
	import { PrismicPreview } from '@prismicio/svelte/kit';
	import { page } from '$app/stores';
	import { repositoryName } from '$lib/prismicio';
	const settings = $page.data.settings.data;
	import '../app.css';
</script>

<svelte:head>
	<title>{$page.data.title}</title>

	<!-- Meta Title -->
	{#if $page.data.meta_title}
		<meta name="og:title" content={$page.data.meta_title} />
	{:else if settings.site_title}
		<meta name="og:title" content={settings.meta_title} />
	{/if}

	<!-- Meta Desecription  -->
	{#if $page.data.meta_description}
		<meta name="description" content={$page.data.meta_description} />
	{:else if settings.meta_description}
		<meta name="description" content={settings.meta_description} />
	{/if}

	<!-- Open Graph -->
	{#if $page.data.meta_image}
		<meta name="og:image" content={$page.data.meta_image} />
		<meta name="twitter:card" content="summary_large_image" />
	{:else if settings.meta_image}
		<meta name="og:image" content={settings.meta_image} />
		<meta name="twitter:card" content="summary_large_image" />
	{/if}

	<script
		async
		defer
		src="https://static.cdn.prismic.io/prismic.js?new=true&repo=prismic-starter-base"
	></script>
</svelte:head>

<main class="bg-surface text-ink">
	<slot />
</main>
<PrismicPreview {repositoryName} />
