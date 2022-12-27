<script lang="ts">
	import classnames from 'classnames';

	type Text = 'h1' | 'h2' | 'h3' | 'h4' | 'h5' | 'p' | 'small';

	export let size: Text = 'p';
</script>

<svelte:element this={size} class={classnames('text', `text--${size}`)}>
	<slot />
</svelte:element>

<style lang="scss">
	.text {
		line-height: 1.5;
		font-size: 16px;
		font-weight: normal;

		&--h1 {
			font-weight: bold;
			font-size: 32px;
		}
		&--h2 {
			font-weight: bold;
			font-size: 24px;
		}
		&--h3 {
			font-weight: bold;
			font-size: 20px;
		}
		&--h4 {
			font-weight: bold;
			font-size: 18px;
		}
		&--h5 {
			font-weight: bold;
		}
		&--small {
			font-size: 14px;
		}
	}
</style>
