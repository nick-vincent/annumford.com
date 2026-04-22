<script lang="ts">
	let { playing = false, onClick } = $props();
</script>

<button class="toggle-audio" aria-label={playing ? 'Pause' : 'Play'} onclick={onClick}>
	{#if playing}
		<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 80 80"
			><path
				d="M56.25,11.66h-12.5c-0.464,0-0.84,0.376-0.84,0.84v55c0,0.464,0.376,0.84,0.84,0.84h12.5c0.464,0,0.84-0.376,0.84-0.84v-55   C57.09,12.036,56.714,11.66,56.25,11.66z"
			/><path
				d="M36.25,11.66h-12.5c-0.464,0-0.84,0.376-0.84,0.84v55c0,0.464,0.376,0.84,0.84,0.84h12.5c0.464,0,0.84-0.376,0.84-0.84v-55   C37.09,12.036,36.714,11.66,36.25,11.66z"
			/>
		</svg>
	{:else}
		<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 333 333">
			<polygon points="58,42 167,104 275,167 167,229 58,292 58,167" />
		</svg>
	{/if}
</button>

<style>
	.toggle-audio {
		flex-shrink: 0;
		display: flex;
		width: 1.5rem;
		height: 1.5rem;
		align-items: center;
		justify-content: center;
	}
</style>
