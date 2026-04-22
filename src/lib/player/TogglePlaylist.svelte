<script lang="ts">
	let { open = false, onClick } = $props();
</script>

<button
	class="toggle-playlist"
	aria-label={open ? 'Close playlist' : 'Open playlist'}
	aria-expanded={open ? 'true' : 'false'}
	aria-controls="drawer"
	aria-haspopup="true"
	onclick={onClick}
>
	{#if open}
		<svg
			class="close-icon"
			xmlns="http://www.w3.org/2000/svg"
			version="1.1"
			viewBox="0 0 100 100"
			xml:space="preserve"
		>
			<polygon
				points="96.5,20.5 79.5,3.5 50,33 20.5,3.5 3.5,20.5 33,50 3.5,79.5 20.5,96.5 50,67 79.5,96.5 96.5,79.5 67,50 "
			/>
		</svg>
	{:else}
		<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
			<rect x="38" y="26" width="40" height="8" />
			<rect x="38" y="46" width="40" height="8" />
			<rect x="38" y="66" width="40" height="8" />
			<rect x="22" y="26" width="8" height="8" />
			<rect x="22" y="46" width="8" height="8" />
			<rect x="22" y="66" width="8" height="8" />
		</svg>
	{/if}
</button>

<style>
	.toggle-playlist {
		flex-shrink: 0;
		display: flex;
		width: 2rem;
		height: 2rem;
		align-items: center;
		justify-content: center;
	}

	.close-icon {
		width: 1rem;
		height: 1rem;
	}
</style>
