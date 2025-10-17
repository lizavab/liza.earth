<script lang="ts">
	import BlueskyIcon from './icons/BlueskyIcon.svelte';
	import GitHubIcon from './icons/GitHubIcon.svelte';
	import LinkedInIcon from './icons/LinkedInIcon.svelte';

	interface Props {
		href: string;
	}

	const { href }: Props = $props();

	const medium = $derived.by(() => {
		if (href.includes('github.com')) {
			return 'github';
		}
		if (href.includes('bsky.app')) {
			return 'bluesky';
		}
		if (href.includes('linkedin.com')) {
			return 'linkedin';
		}
		return 'unknown';
	});

	const Icon = $derived(
		{
			github: GitHubIcon,
			bluesky: BlueskyIcon,
			linkedin: LinkedInIcon,
			unknown: undefined
		}[medium]
	);
</script>

<a {href} target="_blank" class="text-main-500 hover:text-main-400">
	{#if Icon}
		<Icon class="size-6" />
	{:else}
		{medium}
	{/if}
</a>
