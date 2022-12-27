<script lang="ts">
	import { flip } from 'svelte/animate';
	import Box from './box.svelte';
	import Collapse from './collapse.svelte';
	import Stack from './stack.svelte';
	import Text from './text.svelte';

	interface Account {
		id: string;
		name?: string;
		user?: string;
		password?: string;
	}
	export let items: Account[] = [];

	let expanded = new Set();

	function handleToggle(index: number): void {
		expanded.has(index) ? expanded.delete(index) : expanded.add(index);
		expanded = expanded;
	}
</script>

<ul>
	{#each items as item, index (item.id)}
		<li>
			<Box card padding="s">
				<Stack line justify="space-between">
					<Text size="h3">{item.name}</Text>
					<Text size="h3">
						<button on:click={() => handleToggle(index)}>
							<i class="fa-solid fa-magnifying-glass" />
						</button>
					</Text>
				</Stack>
				<Collapse open={expanded.has(index)}>
					<Box padding={{ top: 's' }}>
						<Stack size="xs">
							<Stack line size="xxs">
								<Text size="h4">User:</Text>
								<Text>{item.user}</Text>
							</Stack>
							<Stack line size="xxs">
								<Text size="h4">Password:</Text>
								<Text>{item.password}</Text>
							</Stack>
						</Stack>
					</Box>
				</Collapse>
			</Box>
		</li>
	{/each}
</ul>

<style type="scss">
	ul {
		display: flex;
		flex-direction: column;
		gap: var(--spacing-s);
	}
</style>
