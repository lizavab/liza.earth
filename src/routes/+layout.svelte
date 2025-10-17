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

<div class="flex h-full flex-col items-center gap-2 bg-main-50 bg-pattern p-8">
	<header class="flex w-full max-w-2xl flex-col items-center gap-6 text-center">
		<img
			src="/andri.jpg"
			alt="Andri Soone"
			width="160"
			height="160"
			class="rounded-full shadow-md shadow-main-700/25"
		/>
		<div class="flex flex-col gap-2">
			<h1 class="text-2xl font-semibold text-accent-700">Andri Soone</h1>
			<p class="text-base text-main-600">Full snack developer</p>
		</div>
		<nav class="flex w-full justify-between gap-2">
			<div class="flex gap-2">
				<NavLink href="/" label="/" />
				<NavLink href="/projects" label="/projects" />
				<NavLink href="/now" label="/now" />
				<NavLink href="/uses" label="/uses" />
			</div>
			<div class="flex gap-3">
				<SocialLink href="https://github.com/ndri" />
				<SocialLink href="https://www.linkedin.com/in/andrisoone/" />
				<SocialLink href="https://bsky.app/profile/andri.io" />
			</div>
		</nav>
	</header>
	<main
		class="prose w-full max-w-2xl rounded-xl border-2 border-main-200 bg-white p-8 text-main-700 prose-theme"
	>
		{@render children?.()}
	</main>
</div>
