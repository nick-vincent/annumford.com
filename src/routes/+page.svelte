<script lang="ts">
	import logo from '$lib/images/logo.png?enhanced';
	import photo from '$lib/images/photo.png?enhanced';
</script>

<svelte:head>
	<title>Annum Ford</title>
	<meta
		name="description"
		content="Formed in the early aughts by life-long friends, Annum Ford blended punk, hardcore, grunge, & indie influences with haunting melodies about identity and alienation in the human condition."
	/>
</svelte:head>

<section>
	<h1>
		<enhanced:img src={logo} alt="Annum Ford" />
	</h1>

	<p class="date">2004 – 2007</p>

	<figure>
		<enhanced:img src={photo} alt="The members of Annum Ford" />
		<figcaption>
			<span class="no-wrap">Mike Reilly, Nick Whalen,</span>
			<span class="no-wrap">Jon Losey, & Nick Vincent</span>
		</figcaption>
	</figure>

	<p>
		Formed in the early aughts by life-long friends,
		<span class="no-wrap">Annum Ford</span> blended punk, hardcore, grunge, & indie influences with haunting
		melodies about identity and alienation in the human condition.
	</p>

	<p>
		<a href="mailto:annumford@gmail.com">annumford@gmail.com</a>
	</p>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
</style>
