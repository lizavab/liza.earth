<script lang="ts">
	import type { ClassValue } from 'svelte/elements';

	interface Props {
		class?: ClassValue;
	}

	const { class: className }: Props = $props();
</script>

<svg
	xmlns="http://www.w3.org/2000/svg"
	fill="currentColor"
	viewBox="0 0 24 24"
	class={className}
	aria-hidden="true"
	data-slot="icon"
	role="img"
>
	<path
		d="M4.428 17.401l11.094 3.55L20.5 5.881a.35.35 0 0 0-.543-.386zm-.736-.864l5.478-4.196-6.578-7.755zm15.48-3.024l-2.036 6.156 6.76-6.517c.243-.234.028-.64-.302-.57zM.455 7.116l1.39-.104-.201-2.317L.106 6.425c-.25.282-.027.719.349.691zm8.122 2.826l1.484 1.716 3.26-2.499-1.917-5.933c-.075-.234-.405-.237-.485-.006z"
	/>
</svg>
