<script lang="ts">
	import classnames from 'classnames';

	interface Padding {
		horizontal?: App.Sizes;
		vertical?: App.Sizes;
		top?: App.Sizes;
		bottom?: App.Sizes;
		left?: App.Sizes;
		right?: App.Sizes;
	}

	export let padding: string | Padding | undefined = undefined;
	export let tabletPadding: string | Padding | undefined = undefined;

	function getPaddingArray(padding?: Padding | string): string[] {
		if (padding === undefined) return [];
		if (typeof padding === 'string') {
			return [`box--padding-${padding}`];
		}
		return Object.keys(padding).map(
			(key) => `box--padding-${key}-${padding[key as keyof Padding]}`
		);
	}

	export let card = false;
</script>

<div
	class={classnames('box', ...getPaddingArray(padding), ...getPaddingArray(tabletPadding))}
	class:card
>
	<slot />
</div>

<style lang="scss">
	$directions: 'top', 'right', 'bottom', 'left';

	.box {
		@each $size-name, $size-value in $sizes {
			&--padding-#{$size-name} {
				padding: var(--spacing-#{$size-name});
			}
		}
		@each $size-name, $size-value in $sizes {
			&--padding-horizontal-#{$size-name} {
				padding-left: var(--spacing-#{$size-name});
				padding-right: var(--spacing-#{$size-name});
			}
		}
		@each $size-name, $size-value in $sizes {
			&--padding-vertical-#{$size-name} {
				padding-top: var(--spacing-#{$size-name});
				padding-bottom: var(--spacing-#{$size-name});
			}
		}

		@each $direction in $directions {
			@each $size-name, $size-value in $sizes {
				&--padding-#{$direction}-#{$size-name} {
					padding-#{$direction}: var(--spacing-#{$size-name});
				}
			}
		}

		@include breakpoint-tablet {
			@each $size-name, $size-value in $sizes {
				&--tablet-padding-#{$size-name} {
					padding: var(--spacing-#{$size-name});
				}
			}
			@each $size-name, $size-value in $sizes {
				&--tablet-padding-horizontal-#{$size-name} {
					padding-left: var(--spacing-#{$size-name});
					padding-right: var(--spacing-#{$size-name});
				}
			}
			@each $size-name, $size-value in $sizes {
				&--tablet-padding-vertical-#{$size-name} {
					padding-top: var(--spacing-#{$size-name});
					padding-bottom: var(--spacing-#{$size-name});
				}
			}
			@each $direction in $directions {
				@each $size-name, $size-value in $sizes {
					&--tablet-padding-#{$direction}-#{$size-name} {
						padding-#{$direction}: var(--spacing-#{$size-name});
					}
				}
			}
		}

		&.card {
			background-color: var(--color-background-secondary);
			border-radius: var(--spacing-xs);
		}
	}
</style>
