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
		d="M4.416 2.25c-1.197 0-2.166.969-2.166 2.166v15.168c0 1.197.969 2.166 2.166 2.166h15.168c1.197 0 2.166-.969 2.166-2.166V4.416c0-1.197-.969-2.166-2.166-2.166H4.416zm2.262 2.709c.95 0 1.719.776 1.719 1.732s-.769 1.732-1.719 1.732-1.719-.776-1.719-1.732.769-1.732 1.719-1.732zm8.947 4.406c1.991 0 3.416 1.217 3.416 3.732v5.943h-2.893v-4.928c0-1.351-.514-2.107-1.584-2.107-1.164 0-1.771.787-1.771 2.107v4.928h-2.789V9.652h2.789v1.266s.84-1.553 2.832-1.553zm-10.387.287h2.908v9.389H5.238V9.652z"
	/>
</svg>
