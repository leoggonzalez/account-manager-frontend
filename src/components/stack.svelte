<script lang="ts">
	import classnames from 'classnames';

	export let size: App.Sizes | undefined = undefined;
	export let tabletSize: App.Sizes | undefined = undefined;
	export let desktopSize: App.Sizes | undefined = undefined;
	export let align: App.Align | undefined = undefined;
	export let justify: App.Justify | undefined = undefined;
	export let tabletJustify: App.Justify | undefined = undefined;
	export let desktopJustify: App.Justify | undefined = undefined;
	export let line = false;
	export let tabletLine = false;
	export let desktopLine = false;
	export let reverse = false;
</script>

<div
	class={classnames(
		'stack',
		size && `stack--${size}`,
		tabletSize && `stack--tablet-${tabletSize}`,
		desktopSize && `stack--desktop-${desktopSize}`,
		align && `stack--align-${align}`,
		justify && `stack--justify-${justify}`,
		tabletJustify && `stack--tablet-justify-${tabletJustify}`,
		desktopJustify && `stack--desktop-justify-${desktopJustify}`
	)}
	class:stack--line={line}
	class:stack--tablet-line={tabletLine}
	class:stack--desktop-line={desktopLine}
	class:stack--reverse={reverse}
>
	<slot />
</div>

<style lang="scss">
	.stack {
		display: flex;
		flex-direction: column;
		gap: var(--spacing-m);
		width: 100%;

		> * {
			min-width: 0;
		}

		&--reverse {
			flex-direction: column-reverse;
		}

		&--inline {
			display: inline-flex;
			width: auto;
			flex-shrink: 0;
		}

		&--line {
			flex-direction: row;
			align-items: center;
			&.stack--justify-center {
				justify-content: center;
			}
			&.stack--justify-right {
				justify-content: flex-end;
			}
		}

		&--justify-left {
			align-items: flex-start;
		}

		&--justify-center {
			align-items: center;
		}

		&--justify-right {
			align-items: flex-end;
		}

		&--justify-space-between {
			justify-content: space-between;
		}

		&--justify-space-around {
			justify-content: space-around;
		}

		&--align-top {
			align-items: flex-start;
		}

		&--align-stretch {
			align-items: stretch;
		}

		&--align-bottom {
			align-items: flex-end;
		}

		&--align-space-between {
			height: 100%;
			justify-content: space-between;
		}

		&--zero {
			gap: 0;
		}

		&--wrap {
			flex-wrap: wrap;
		}

		&--clickable {
			cursor: pointer;
		}

		@each $size-name, $size-value in $sizes {
			&--#{$size-name} {
				gap: var(--spacing-#{$size-name});
			}
		}

		@each $size-name, $size-value in $sizes {
			&--padding-top-#{$size-name} {
				padding-top: var(--spacing-#{$size-name});
			}
		}

		@include breakpoint-tablet {
			@each $size-name, $size-value in $sizes {
				&--tablet-#{$size-name} {
					gap: var(--spacing-#{$size-name});
				}
			}
			&--tablet-line {
				flex-direction: row;
				align-items: center;
				&.stack--justify-center {
					justify-content: center;
				}
				&.stack--align-top {
					align-items: flex-start;
				}
				&.stack--align-stretch {
					align-items: stretch;
				}
			}
			&--line,
			&--tablet-line {
				&.stack--tablet-justify-left {
					justify-content: flex-start;
				}
				&.stack--tablet-justify-right {
					justify-content: flex-end;
				}
				&.stack--tablet-justify-center {
					justify-content: center;
				}
				&.stack--tablet-reverse {
					flex-direction: row-reverse;
				}
			}
			&--tablet-justify-left {
				align-items: flex-start;
			}
			&--tablet-justify-center {
				align-items: center;
			}
			&--tablet-justify-right {
				align-items: flex-end;
			}
			&--tablet-inline {
				display: inline-flex;
				width: auto;
				flex-shrink: 0;
			}
		}
		@include breakpoint-desktop {
			@each $size-name, $size-value in $sizes {
				&--desktop-#{$size-name} {
					gap: var(--spacing-#{$size-name});
				}
			}
			&--desktop-reverse {
				flex-direction: row-reverse;
				&.stack--desktop-justify-left {
					justify-content: flex-end;
				}
			}
			&--desktop-line {
				flex-direction: row;
				align-items: center;
				&.stack--desktop-align-top {
					align-items: flex-start;
				}
			}
			&--line,
			&--tablet-line {
				&.stack--desktop-justify-right {
					justify-content: flex-end;
				}
			}
			&--desktop-justify-left {
				align-items: flex-start;
			}
			&--desktop-justify-center {
				align-items: center;
			}
			&--desktop-justify-right {
				align-items: flex-end;
			}
		}
	}
</style>
