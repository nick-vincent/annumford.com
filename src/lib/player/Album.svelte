<script lang="ts">
	import album from '$lib/images/of-analog.png?enhanced';
</script>

<div class="album">
	<enhanced:img class="cover" src={album} alt="Of Analog album cover" />
	<div class="info">
		<div class="title">Of Analog</div>
		<div class="year">Nov 24 2006</div>
	</div>
</div>

<style>
	.album {
		background-color: rgb(6, 3, 2, 0.5);
		border-right: 1px solid var(--color-border);
		text-align: center;
		flex-grow: 0;
	}

	.cover {
		display: block;
		width: clamp(8rem, 36dvw, 16rem);
		aspect-ratio: 1;
	}

	.info {
		margin: 0 auto;
		padding: 1rem 0;
	}

	.title {
		color: var(--color-text);
		letter-spacing: 0.25em;
		font-weight: 900;
		font-size: 0.75rem;
		line-height: 1.5rem;
		text-transform: uppercase;
	}

	.year {
		font-weight: 600;
		font-size: 0.75rem;
		letter-spacing: 0.1em;
		text-transform: uppercase;
		color: var(--color-text-muted);
	}
</style>
