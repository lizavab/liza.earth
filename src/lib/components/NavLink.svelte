<script lang="ts">
	import { page } from '$app/state';

	interface Props {
		href: string;
		label: string;
	}

	const { href, label }: Props = $props();

	const currentPath = $derived(page.url.pathname);
	const active = $derived(currentPath === href);
</script>

<a
	{href}
	class={[
		'rounded-md px-2 py-1 text-sm',
		active
			? ['bg-accent-100 text-accent-800', 'dark:bg-accent-700 dark:text-accent-50']
			: [
					'bg-transparent text-main-700',
					'hover:bg-accent-100 hover:text-accent-800',
					'active:bg-accent-200 active:text-accent-900',
					'dark:text-main-200',
					'dark:hover:bg-accent-700 dark:hover:text-accent-50',
					'dark:active:bg-accent-800 dark:active:text-accent-100'
				]
	]}
>
	{label}
</a>
