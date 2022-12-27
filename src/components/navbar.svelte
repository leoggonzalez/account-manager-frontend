<script>
	import Box from './box.svelte';
	import Container from './container.svelte';

	const links = ['home', 'settings'];
</script>

<nav class="navbar">
	<Container>
		<Box padding={{ vertical: 's' }}>
			<ul>
				{#each links as link}
					<li><a href="/{link}">{link}</a></li>
				{/each}
			</ul>
		</Box>
	</Container>
</nav>

<style>
	.navbar {
		background-color: var(--color-background-secondary);
		position: fixed;
		bottom: 0;
	}
</style>
