<script>
	import Box from './box.svelte';
	import Container from './container.svelte';
	import Stack from './stack.svelte';
	import Text from './text.svelte';

	const links = [
		{
			icon: 'fa-solid fa-house',
			title: 'Home',
			path: '/'
		},
		{
			icon: 'fa-solid fa-gear',
			title: 'Settings',
			path: '/settings'
		}
	];
</script>

<nav class="navbar">
	<Container>
		<Box padding={{ vertical: 's' }}>
			<Stack line justify="space-around">
				{#each links as link}
					<a class="navbar__link" href={link.path}>
						<Stack size="xxxs" justify="center">
							<i class={link.icon} />
							<Text size="small">{link.title}</Text>
						</Stack>
					</a>
				{/each}
			</Stack>
		</Box>
	</Container>
</nav>

<style lang="scss">
	.navbar {
		background-color: var(--color-background-secondary);
		position: fixed;
		bottom: 0;

		&__link {
			color: inherit;
			display: block;
			text-decoration: none;
		}
	}
</style>
