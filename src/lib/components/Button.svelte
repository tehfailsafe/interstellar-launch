<script lang="ts">
	import { PrismicLink } from '@prismicio/svelte';

	let className: string = '';
	export { className as class };

	export let variant: 'primary' | 'secondary' = 'primary';

	const baseClass =
		'w-full flex items-center justify-center px-3 py-3 md:w-auto md:px-5 md:py-3 rounded';
	const variantClasses = {
		primary: 'bg-surface-primary text-surface-primary-ink',
		secondary: 'border border-border/50 text-gray-800',
		undefined: ''
	};
</script>

<PrismicLink
	class={`${baseClass} ${variantClasses[variant]} ${className}`}
	field={$$restProps.field}
	{...$$restProps}
>
	<slot />
</PrismicLink>
