<script lang="ts">
	import Apple from '$lib/streaming/apple.svelte';
	import Spotify from '$lib/streaming/spotify.svelte';
	import YouTube from '$lib/streaming/youtube.svelte';
	import Tidal from '$lib/streaming/tidal.svelte';
	import Amazon from '$lib/streaming/amazon.svelte';
	import Pandora from '$lib/streaming/pandora.svelte';
	import SoundCloud from '$lib/streaming/soundcloud.svelte';
</script>

<header>
	<ul class="links">
		<li><Apple /></li>
		<li><Spotify /></li>
		<li><Tidal /></li>
		<li><YouTube /></li>
		<li><Pandora /></li>
		<li><Amazon /></li>
		<li><SoundCloud /></li>
	</ul>
</header>

<style>
	header {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		background-color: rgb(110, 53, 38, 0.75);
		backdrop-filter: blur(0.75rem);
		border-bottom: 1px solid var(--color-border);
		box-shadow: 0 0.5rem 0.5rem rgba(0, 0, 0, 0.25);
	}

	.links {
		list-style: none;
		display: flex;
		gap: 1rem;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		width: 100%;
		padding: 0.75rem 1rem;
		margin: 0 auto;
		font-weight: 600;
		text-transform: uppercase;
		line-height: 1;
	}
	li {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 1.75rem;
		height: 1.75rem;
	}
</style>
