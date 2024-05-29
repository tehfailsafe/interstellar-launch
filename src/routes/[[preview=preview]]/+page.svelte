<script>
	import { SliceZone } from '@prismicio/svelte';

	import { components } from '$lib/slices';
	import Hero from '$lib/slices/Hero/index.svelte';
	export let data;
</script>

<SliceZone slices={data.page.data.slices} {components} />
