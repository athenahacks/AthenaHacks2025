<script lang="ts">
	import Header from '../Header.svelte';
	import data from '$lib/data/faqs.yml';
	import FaqDetails from '../FaqDetails.svelte';
</script>

<section id="faqs">
	<div class="content">
		<div class="questions">
			<Header>FAQs</Header>
			{#each data.faq as qa}
				<FaqDetails question={qa.question} answer={qa.answer} />
			{/each}
		</div>
		<div class="image">
			<figure>
				<img src="/images/shovel_owl.png" alt="Shovel Owl" />
				<figcaption>
					Don’t see your question? Hit us up at <a href="mailto:athenahacks@gmail.com"
						>athenahacks@gmail.com</a
					>!
				</figcaption>
			</figure>
			<img class="flower" src="/images/flower.png" alt="pink flower" />
		</div>
	</div>
</section>

<style lang="scss">
	.content {
		display: flex;
		gap: 4em;
		flex-wrap: wrap;

		.questions {
			flex: 2;
		}

		.flower {
			padding-top: 150px;
			padding-right: 20px;
		}

		.image {
			text-align: right;
			flex: 1;

			figure {
				margin: 0;
				margin-top: 6em;

				figcaption {
					margin-top: 2em;
				}
			}
		}

		@include respond-to('medium') {
			flex-direction: column;
			.image {
				width: 60%;
				margin: auto;

				figure {
					text-align: center;
					margin-top: 0;
				}

				img {
					width: 100%;
				}
			}
		}

		@include respond-to('small') {
			.image {
				width: 80%;
			}
		}
	}
</style>
