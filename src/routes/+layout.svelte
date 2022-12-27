<script>
	import '../app.scss';
	import Box from '../components/box.svelte';
	import Container from '../components/container.svelte';
	import Navbar from '../components/navbar.svelte';
</script>

<Navbar />
<Container>
	<Box padding={{ top: 'm', bottom: 'l' }}>
		<slot />
	</Box>
</Container>
