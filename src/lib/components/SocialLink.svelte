<script lang="ts">
	import BlueskyIcon from './icons/BlueskyIcon.svelte';
	import GitHubIcon from './icons/GitHubIcon.svelte';
	import GitLabIcon from './icons/GitLabIcon.svelte';
	import LinkedInIcon from './icons/LinkedInIcon.svelte';
	import ManifoldIcon from './icons/ManifoldIcon.svelte';

	interface Props {
		href: string;
	}

	const { href }: Props = $props();

	const medium = $derived.by(() => {
		if (href.includes('github.com')) {
			return 'GitHub';
		}
		if (href.includes('bsky.app')) {
			return 'Bluesky';
		}
		if (href.includes('linkedin.com')) {
			return 'LinkedIn';
		}
		if (href.includes('gitlab.com')) {
			return 'GitLab';
		}
		if (href.includes('manifold.markets')) {
			return 'Manifold';
		}
		return 'unknown';
	});

	const Icon = $derived(
		{
			GitHub: GitHubIcon,
			Bluesky: BlueskyIcon,
			LinkedIn: LinkedInIcon,
			GitLab: GitLabIcon,
			Manifold: ManifoldIcon,
			unknown: undefined
		}[medium]
	);
</script>

<a
	{href}
	target="_blank"
	class={[
		'text-main-500 hover:text-main-400 active:text-main-300',
		'dark:text-main-200 dark:hover:text-main-300 dark:active:text-main-400'
	]}
	title={medium}
>
	{#if Icon}
		<Icon class="size-6" />
	{:else}
		{medium}
	{/if}
</a>
