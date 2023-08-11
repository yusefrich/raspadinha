<script>
	// import Header from './Header.svelte';
	// import Header from '$lib/components/atoms/Header.svelte';
	import './styles.css';
	import "@fontsource/montserrat/800-italic.css";
</script>

<div class="app">
	<main>
		<slot />
	</main>
	<!-- <Header />


	<footer>
		<p>visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit</p>
	</footer> -->
</div>

<style>
	main {
		/* border: solid 10px red; */
	}
	/* .app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	} */
</style>
