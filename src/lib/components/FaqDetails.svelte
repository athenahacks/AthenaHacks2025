<!-- Individual dropdown component used in Faqs.svelte -->
<script lang="ts">
	export let question: string;
	export let answer: string;
</script>

<div class="faq-details">
	<details>
		<summary><span role="term">{question}</span></summary>
	</details>
	<div role="definition" class="content">
		<p>{@html answer}</p>
	</div>
</div>

<style lang="scss">
	.faq-details {
		margin-bottom: 1.5em;
		filter: drop-shadow(0.3em 0.3em 0 $brown);
		transition: all 0.4s ease-out;

		&:hover {
			transform: rotate(-0.5deg);
		}
	}

	details {
		outline: 2px solid $brown;
		border-radius: 0.75em 0.75em 0em 0.75em;
		background-color: $lime;
		overflow: hidden;
		color: $brown;

		summary {
			display: block;
			transition: background-color 200ms ease-in;

			&::-webkit-details-marker {
				display: none;
			}

			&:hover {
				cursor: pointer;
			}

			span {
				font-size: 1.1rem;
				position: relative;
				display: flex;
				align-items: center;
				font-family: 'Lilita One', sans-serif;
				padding: 0.75em 1em;

				&:before {
					content: '>';
					font-size: 1.1rem;
					display: flex;
					align-items: center;
					margin-right: 0.75rem;
					transition: rotate 200ms ease-out;
				}
			}
		}

		&[open] {
			background-color: pink;
			+ .content {
				max-height: 800px; /* Set a max-height value enough to show all the content */
				outline: 2px solid $brown;
				transition:
					max-height 300ms cubic-bezier(0.88, 0.01, 0.74, 0.85),
					outline 0ms linear;
			}
			span::before {
				rotate: 90deg;
			}
		}
	}

	.content {
		margin-top: 2px;
		background-color: #F6E7DD;
		border-radius: 0.75em 0em 0.9em 0.9em;
		outline: 3px solid transparent;

		max-height: 0;
		box-sizing: border-box;
		overflow: hidden;
		transition:
			max-height 300ms ease-in-out,
			outline 0ms 300ms linear;

		p {
			padding: 1em 2em 1.5em;
			margin: 0;
		}
	}
</style>
