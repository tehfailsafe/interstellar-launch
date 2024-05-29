<script lang="ts">
	import { PrismicLink } from '@prismicio/svelte';

	let className = undefined;
	export { className as class };

	export let variant: 'primary' | 'secondary' = 'primary';

	const baseClass = 'justify-center px-5 py-3 rounded-lg md:px-24 md:py-4';
	const variantClasses = {
		primary: 'bg-white text-primary-500',
		secondary: 'border border-white/50 text-white'
	};
</script>

<PrismicLink
	class={`${baseClass} ${variantClasses[variant]} ${className}`}
	field={$$restProps.field}
	{...$$restProps}
>
	<slot />
</PrismicLink>
