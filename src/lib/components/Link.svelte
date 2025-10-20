<script lang="ts">
	import type { Snippet } from 'svelte';
	// import { ArrowTopRightOnSquareIcon as SmIcon } from '@sidekickicons/svelte/16/solid';
	import { ArrowTopRightOnSquareIcon as MdIcon } from '@sidekickicons/svelte/16/solid';
	// import { ArrowTopRightOnSquareIcon as LgIcon } from '@sidekickicons/svelte/24/solid';

	interface Props {
		href: string;
		children: Snippet;
	}

	const { href, children }: Props = $props();

	const newTab = $derived(href.startsWith('http'));
</script>

<a
	{href}
	target={newTab ? '_blank' : undefined}
	rel={newTab ? 'noopener noreferrer' : undefined}
	class={[
		'inline-flex flex-wrap items-center gap-[0.15em]',
		'hover:text-(--tw-prose-links-hover)',
		'active:text-(--tw-prose-links-active)',
		'dark:hover:text-(--tw-prose-invert-links-hover)',
		'dark:active:text-(--tw-prose-invert-links-active)'
	]}
>
	{@render children()}
	{#if newTab}
		<MdIcon class="inline size-[calc(8em/7)] underline" />
	{/if}
</a>
