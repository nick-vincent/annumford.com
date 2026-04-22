<script lang="ts">
	let { onSelect, index, tracks = [] } = $props();
</script>

<ol class="playlist">
	{#each tracks as track (track.src)}
		<li>
			<button
				class={track.title === tracks[index]?.title ? 'selected' : ''}
				onclick={() => {
					onSelect?.(track);
				}}
			>
				{track.title}
			</button>
		</li>
	{/each}
</ol>

<style>
	.playlist {
		display: block;
		list-style-position: inside;
		width: 100%;
		font-weight: 500;
		font-size: 0.75rem;
		text-transform: uppercase;
		list-style: none;
		background-color: rgb(6, 3, 2, 0.75);
		overflow: auto;
	}

	.playlist li:not(:last-child) {
		border-bottom: 1px solid var(--color-border);
	}

	.playlist button.selected {
		color: var(--color-icon-hover);
		background-color: rgb(110, 53, 38, 0.5);
	}

	.playlist button {
		display: block;
		align-items: center;
		justify-content: start;
		flex-direction: row;
		align-items: center;
		width: 100%;
		color: var(--color-text);
		text-decoration: none;
		text-align: left;
		border-radius: 0;
		padding: 1rem 1rem;
		outline-offset: 0;
		letter-spacing: 0.1em;
		gap: 0.5rem;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	@media (hover: hover) {
		.playlist button:not(.selected):hover {
			color: var(--color-icon-hover);
			background-color: rgb(110, 53, 38, 0.25);
		}
	}
</style>
