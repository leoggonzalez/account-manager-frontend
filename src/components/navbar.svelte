<script>
	import Container from './container.svelte';
</script>

<nav class="navbar">
	<Container>
		<ul>
			<li>
				<a href="/">Home</a>
			</li>
			<li>
				<a href="/accounts">Accounts</a>
			</li>
		</ul>
	</Container>
</nav>

<style>
	.navbar {
		background-color: var(--color-background-secondary);
	}
</style>
