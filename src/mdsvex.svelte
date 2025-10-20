<script lang="ts" module>
	import a from '$lib/components/Link.svelte';
	export { a };
</script>

<script lang="ts">
	let props = $props();
</script>

{@render props.children?.()}
