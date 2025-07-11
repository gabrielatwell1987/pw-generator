<script>
</script>

<main>
	<slot />
</main>

<style>
	:global(body) {
		background: white;
	}

	main {
		display: grid;
		place-items: center;
		height: 100vh;
		padding: 1rem;
		box-sizing: border-box;
	}
</style>
