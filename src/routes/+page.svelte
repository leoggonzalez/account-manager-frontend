<script lang="ts">
	import AccountList from '../components/account_list.svelte';
	import Stack from '../components/stack.svelte';
	import Text from '../components/text.svelte';

	const accounts = [
		{
			id: '1',
			name: 'Github',
			user: 'leo@test.com',
			password: 'github1234'
		},
		{
			id: '2',
			name: 'Gmail',
			user: 'leo@test.com',
			password: 'github1234'
		}
	];
</script>

<Stack>
	<header>
		<Text size="h1">Account manager</Text>
	</header>
	<section>
		<Stack size="s">
			<Text size="h2">Accounts</Text>
			<AccountList items={accounts} />
		</Stack>
	</section>
</Stack>
