<script lang="ts">
	import ButtonLink from './button-link.svelte';

	import Card from './card.svelte';
	import Headline from './headline.svelte';
   export let githubHref: string = '/'
	export let href: string = '/';
	export let imgAlt: string = 'placeholder card';
	export let imgURL: string =
		'https://cdn.pixabay.com/photo/2017/06/19/11/27/the-parthenon-2419027_960_720.jpg';
	export let title = 'Placeholder';
</script>

<Card>
	<header>
		<Headline {title} headlineType="h2" />
		<img src={imgURL} alt={imgAlt} />
	</header>
	<main>
		<section class="description">
			<p>
				{#if title === 'Placeholder'}
					Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas quae
					quam vel laudantium id repellendus adipisci ipsum! Voluptates illo eos
					delectus debitis quam totam explicabo voluptatem. Accusamus ipsam
					error fugiat.
				{:else}
					<slot />
				{/if}
			</p>
		</section>
	</main>
	<footer>
		<ButtonLink content={'OPEN'} {href} />
		<ButtonLink content={'Github'} href="{githubHref}" blank={true} outline={true} />
	</footer>
</Card>

<style lang="scss">
	img {
		width: 100%;
		height: 13rem;
		object-fit: cover;
	}

	header {
		width: 100%;
		display: flex;
		flex-direction: column;
		text-align: center;
		justify-content: space-between;
		height: 18rem;
		background-color: var(--secondary-dark);
	}

	main {
		padding: 0.5rem;
		margin-bottom: 4rem;

		p {
			margin: 1rem 1rem 0.5rem;
		}
	}

	footer {
		position: absolute;
		bottom: 0;
		display: flex;
		justify-content: flex-start;
      gap: 1rem;
		margin-block: 1rem;
		padding-inline: 1.5rem;
		width: 100%;
	}
</style>
