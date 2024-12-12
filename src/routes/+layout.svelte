<script>
	/** @type {{children?: import('svelte').Snippet}} */
	let { children } = $props();</script>

<main>
	{@render children?.()}
</main>

<style>
	:global(body) {
		background: white;
	}

	main {
		display: grid;
		place-items: center;
		height: 100vh;
	}
</style>
