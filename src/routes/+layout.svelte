<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import NavLink from '$lib/components/NavLink.svelte';
	import SocialLink from '$lib/components/SocialLink.svelte';
	import data from '$lib/data.json';
	import { page } from '$app/state';

	let { children } = $props();

	const currentPath = $derived(page.url.pathname);
	const pageTitle = $derived(data.nav.find((item) => item.href === currentPath)?.label);
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>{pageTitle ? `${pageTitle} • ` : ''}{data.name}</title>
</svelte:head>

<div
	class={[
		'bg-pattern flex h-full flex-col items-center gap-4 bg-main-50 bg-center px-0 pt-8',
		'sm:gap-2 sm:px-8',
		'dark:bg-main-900'
	]}
>
	<header class="flex w-full max-w-2xl flex-col items-center gap-6 text-center">
		{#if data.image}
			<img
				src={data.image}
				alt={data.name}
				width="160"
				height="160"
				class="rounded-full shadow-md shadow-main-700/25"
			/>
		{/if}
		<div class="flex flex-col gap-2">
			<h1 class="text-3xl font-semibold text-accent-700 dark:text-accent-500">{data.name}</h1>
			{#if data.role}
				<p class="text-base text-main-600 dark:text-main-300">{data.role}</p>
			{/if}
		</div>
		<nav class="flex w-full flex-wrap justify-between gap-2 px-4 sm:px-0">
			<div class="flex gap-2">
				{#each data.nav as { href, label } (href)}
					<NavLink {href} {label} />
				{/each}
			</div>
			<div class="flex gap-3 self-end">
				{#each data.socials as href}
					<SocialLink {href} />
				{/each}
			</div>
		</nav>
	</header>
	<main
		class={[
			'h-full w-full max-w-2xl border border-main-200 bg-white px-6 py-8 text-main-700',
			'sm:h-auto sm:rounded-xl sm:px-8',
			'prose prose-sm prose-theme dark:prose-invert prose-headings:font-medium',
			'dark:border-main-800 dark:bg-main-950 dark:text-main-200'
		]}
	>
		{@render children?.()}
	</main>
</div>
