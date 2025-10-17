<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import NavLink from '$lib/components/NavLink.svelte';
	import SocialLink from '$lib/components/SocialLink.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<div
	class={[
		'flex h-full flex-col items-center gap-2 bg-main-50 bg-pattern-light p-4 sm:p-8',
		'dark:bg-main-900 dark:bg-pattern-dark'
	]}
>
	<header class="flex w-full max-w-2xl flex-col items-center gap-6 text-center">
		<img
			src="/andri.jpg"
			alt="Andri Soone"
			width="160"
			height="160"
			class="rounded-full shadow-md shadow-main-700/25"
		/>
		<div class="flex flex-col gap-2">
			<h1 class="text-3xl font-semibold text-accent-700 dark:text-accent-500">Andri Soone</h1>
			<p class="text-base text-main-600 dark:text-main-300">Full snack developer</p>
		</div>
		<nav class="flex w-full flex-wrap justify-between gap-2">
			<div class="flex gap-2">
				<NavLink href="/" label="/" />
				<NavLink href="/projects" label="/projects" />
				<NavLink href="/now" label="/now" />
				<NavLink href="/uses" label="/uses" />
			</div>
			<div class="flex gap-3 self-end">
				<SocialLink href="https://github.com/ndri" />
				<SocialLink href="https://www.linkedin.com/in/andrisoone/" />
				<SocialLink href="https://bsky.app/profile/andri.io" />
			</div>
		</nav>
	</header>
	<main
		class={[
			'w-full max-w-2xl rounded-xl border border-main-200 bg-white p-8 text-main-700',
			'prose prose-theme dark:prose-invert prose-headings:font-medium',
			'dark:border-main-700 dark:bg-main-950 dark:text-main-200'
		]}
	>
		{@render children?.()}
	</main>
</div>
