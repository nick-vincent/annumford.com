<script lang="ts">
	type Track = {
		title: string;
		src: string;
	};

	import { onMount } from 'svelte';
	import { slide } from 'svelte/transition';
	import { quadInOut } from 'svelte/easing';
	import Album from '$lib/player/Album.svelte';
	import Playlist from '$lib/player/Playlist.svelte';
	import ToggleAudio from '$lib/player/ToggleAudio.svelte';
	import TogglePlaylist from '$lib/player/TogglePlaylist.svelte';

	const tracks: Track[] = [
		{ title: 'The Pessimist', src: '/audio/Annum Ford - Of Analog - 01 The Pessimist.mp3' },
		{ title: 'Epiphany', src: '/audio/Annum Ford - Of Analog - 02 Epiphany.mp3' },
		{ title: 'The Nevermind', src: '/audio/Annum Ford - Of Analog - 03 The Nevermind.mp3' },
		{ title: 'To & Fro', src: '/audio/Annum Ford - Of Analog - 04 To & Fro.mp3' },
		{ title: 'Leap', src: '/audio/Annum Ford - Of Analog - 05 Leap.mp3' },
		{ title: 'All Right', src: '/audio/Annum Ford - Of Analog - 06 All Right.mp3' },
		{
			title: 'Ode to the Overboard',
			src: '/audio/Annum Ford - Of Analog - 07 Ode to the Overboard.mp3'
		},
		{ title: 'Sinking', src: '/audio/Annum Ford - Of Analog - 08 Sinking.mp3' },
		{ title: 'Of Analog', src: '/audio/Annum Ford - Of Analog - 09 Of Analog.mp3' },
		{ title: 'The Payoff', src: '/audio/Annum Ford - Of Analog - 10 The Payoff.mp3' }
	];

	let audio: HTMLAudioElement;
	let index = $state(0);
	let open = $state(false);
	let playing = $state(false);
	let currentTime = $state('0:00');
	let totalTime = $state('0:00');

	onMount(() => {
		audio = new Audio();
		audio.src = tracks[index].src;

		audio.addEventListener('loadedmetadata', () => {
			totalTime = durationToString(audio.duration);
		});

		audio.addEventListener('timeupdate', () => {
			totalTime = durationToString(audio.duration);
			currentTime = durationToString(audio.currentTime);
		});

		audio.addEventListener('pause', () => {
			pause();
		});

		audio.addEventListener('play', () => {
			play();
		});

		audio.addEventListener('ended', () => {
			const nextTrackIndex = (index + 1) % tracks.length;
			play(tracks[nextTrackIndex]);
		});
	});

	const durationToString = (duration: number) => {
		const minutes = Math.floor(duration / 60);
		const seconds = Math.floor(duration % 60);
		return `${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
	};

	const play = (track?: Track) => {
		if (track && tracks[index]?.src !== track?.src) {
			totalTime = '0:00';
			index = tracks.findIndex((t) => t.src === track.src);
			audio.src = tracks[index].src;
		}
		audio?.play();
		playing = true;
	};

	const pause = () => {
		audio?.pause();
		playing = false;
	};
</script>

<footer>
	<div class="current-track">
		<ToggleAudio {playing} onClick={() => (playing ? pause() : play())} />
		<div class="song">{tracks[index].title}</div>
		{#if currentTime && totalTime !== 'NaN:NaN'}
			<div class="time">
				<span class="current-time">{currentTime}</span>
				/
				<span class="duration">{totalTime}</span>
			</div>
		{/if}
		<TogglePlaylist
			{open}
			onClick={() => {
				open = !open;
			}}
		/>
	</div>

	{#if open}
		<div
			id="drawer"
			class="drawer"
			in:slide={{ duration: 250, easing: quadInOut }}
			out:slide={{ duration: 250, easing: quadInOut }}
		>
			<Album />
			<Playlist
				{tracks}
				{index}
				onSelect={(track: Track) => {
					play(track);
				}}
			/>
		</div>
	{/if}
</footer>

<style>
	footer {
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		background-color: rgb(110, 53, 38, 0.75);
		backdrop-filter: blur(0.75rem);
		border-top: 1px solid var(--color-border);
		white-space: nowrap;
		box-shadow: 0 -0.5rem 0.5rem rgba(0, 0, 0, 0.25);
	}

	.current-track {
		display: flex;
		gap: 0.5rem;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		padding: 0.5rem 1rem;
		margin: 0 auto;
		font-weight: 600;
		font-size: 0.75rem;
		letter-spacing: 0.1em;
		text-transform: uppercase;
		line-height: 1;
	}

	.song {
		margin-right: auto;
		overflow: hidden;
		text-overflow: ellipsis;
		font-weight: 600;
	}

	.time {
		color: var(--color-text-muted);
		font-feature-settings: 'tnum';
	}

	.drawer {
		display: flex;
		flex-direction: row;
		border: 1px solid var(--color-border);
		max-height: calc(100dvh - 4rem);
		margin: 0 1rem 1rem;
		overflow: hidden;
		border-radius: 0 0 1rem 1rem;
	}
</style>
