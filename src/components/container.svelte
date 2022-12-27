<div class="container">
	<div class="container__content">
		<slot />
	</div>
</div>

<style lang="scss">
	.container {
		display: grid;
		grid-template-columns:
			minmax(var(--container-gap), 1fr)
			0
			minmax(0, 1280px)
			0
			minmax(var(--container-gap), 1fr);

		&__content {
			grid-column: 3/3;
		}
	}
</style>
