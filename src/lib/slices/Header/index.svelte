<script>
	import Button from '$lib/components/Button.svelte';
	import { PrismicLink } from '@prismicio/svelte';
	import { page } from '$app/stores';
	const settings = $page.data.settings.data;

	let isOpen = false;
	const toggleOpen = () => (isOpen = !isOpen);
	const setClose = () => (isOpen = false);
	console.log(isOpen);
</script>

<header class="">
	<nav class="container flex items-center justify-between py-6">
		<a href="/">
			{#if settings.meta_title}
				<div class="font-bold text-xl text-ink">{settings.meta_title}</div>
			{:else}
				<div class="font-bold text-xl bg-red-500 text-white">ADD SITE TITLE</div>
			{/if}
		</a>

		<div class="flex md:hidden">
			<button type="button" on:click={toggleOpen}>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					class="w-6 h-6"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M4 6h16M4 12h16M4 18h16"
					/>
				</svg>
			</button>
		</div>

		<!-- Mobile Nav -->
		<div
			class={`fixed inset-0 bg-surface z-40  px-6 pt-6 flex-col flex items-end md:hidden transition-transform ease-in-out duration-300 ${isOpen ? 'translate-x-0' : 'translate-x-full'}`}
		>
			<div class="flex items-center justify-between w-full">
				<a href="/">
					{#if settings.meta_title}
						<div class="font-bold text-xl text-ink">{settings.meta_title}</div>
					{:else}
						<div class="font-bold text-xl bg-red-500 text-white">ADD SITE TITLE</div>
					{/if}
				</a>
				<button type="button" on:click={setClose}>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="w-6 h-6"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					</svg>
				</button>
			</div>

			<ul class="grid justify-items-start w-full gap-4 text-ink-primary mt-12">
				{#each settings.navigation as item}
					<li class="text-xl">
						<PrismicLink field={item.link}>{item.label}</PrismicLink>
					</li>
				{/each}

				<div class="mt-6 w-full">
					{#each settings.actions as item}
						<li class="">
							<Button class="w-full bg-red-500" field={item.link} variant={item.button_variant}
								>{item.label}</Button
							>
						</li>
					{/each}
				</div>
			</ul>
		</div>

		<!-- Desktop Nav -->
		<ul class="hidden md:flex items-center gap-4 text-ink-primary">
			{#each settings.navigation as item}
				<li>
					<PrismicLink field={item.link}>{item.label}</PrismicLink>
				</li>
			{/each}

			{#if settings.actions && !settings.center_nav}
				{#each settings.actions as item}
					<Button field={item.link} variant={item.button_variant}>{item.label}</Button>
				{/each}
			{/if}
		</ul>

		{#if settings.actions && settings.center_nav}
			<div class="hidden md:block">
				{#each settings.actions as item}
					<Button field={item.link} variant={item.button_variant}>{item.label}</Button>
				{/each}
			</div>
		{/if}
	</nav>
</header>
