<script lang="ts">
	interface Props {
		href: string;
		title: string;
		date: string;
		image?: string;
		tags?: string[];
		target?: '_blank' | '_self';
	}

	const { href, title, date, image, tags = [], target }: Props = $props();
</script>

<a
	{href}
	{target}
	rel={target === '_blank' ? 'noopener noreferrer' : undefined}
	class="group flex flex-col rounded-lg border border-main-200 dark:border-main-700 overflow-hidden hover:border-accent-400 dark:hover:border-accent-500 transition-colors"
>
	<div class="w-full h-48 overflow-hidden bg-main-100 dark:bg-main-800">
		{#if image}
			<img src={image} alt={title} class="w-full h-full object-cover object-center" />
		{:else}
			<div
				class="w-full h-full bg-gradient-to-br from-accent-100 to-accent-200 dark:from-accent-900 dark:to-accent-800 flex items-center justify-center"
			>
				<svg
					class="w-16 h-16 text-accent-600 dark:text-accent-300"
					fill="none"
					stroke="currentColor"
					viewBox="0 0 24 24"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"
					></path>
				</svg>
			</div>
		{/if}
	</div>
	<div class="px-4 py-4">
		<h3
			class="font-medium text-main-800 dark:text-main-100 group-hover:text-accent-600 dark:group-hover:text-accent-400"
		>
			{title}
		</h3>
		<p class="text-sm text-main-500 dark:text-main-400 mt-1">{date}</p>
		{#if tags.length > 0}
			<div class="flex flex-wrap gap-2 mt-3">
				{#each tags as tag}
					<span
						class="text-xs px-2 py-1 rounded-md bg-main-200 text-main-700 dark:bg-main-700 dark:text-main-200"
					>
						{tag}
					</span>
				{/each}
			</div>
		{/if}
	</div>
</a>
