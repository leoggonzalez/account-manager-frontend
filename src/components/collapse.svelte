<script>
	export let open = false;
</script>

<div class="collapse" class:open>
	<div class="collapse__content">
		<slot />
	</div>
</div>

<style lang="scss">
	.collapse {
		display: grid;
		grid-template-rows: 0fr;
		transition: 0.25s;
		overflow: hidden;
		&__content {
			min-height: 0;
		}
		&.open {
			grid-template-rows: 1fr;
		}
	}
</style>
