<script lang="ts">
	import { PrismicLink } from '@prismicio/svelte';

	let className = undefined;
	export { className as class };

	export let variant: 'primary' | 'secondary' = 'primary';

	const baseClass = 'px-5 py-3 rounded';
	const variantClasses = {
		primary: 'bg-surface-primary text-on-primary',
		secondary: 'border border-gray-300/50 text-gray-800',
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
