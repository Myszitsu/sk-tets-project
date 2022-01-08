<script lang="ts">
	import Card from './card.svelte';
	import Headline from './headline.svelte';
	export let title: string;
</script>

<Card>
	<header>
		<Headline headlineType={'h2'} {title}/>
		<slot />
	</header>
	<main>
		<slot name="main" />
	</main>
	<footer>
		<slot name="footer" />
	</footer>
</Card>

<style lang="scss">
	header {
		display: flex;
		flex-direction: column;
		text-align: center;
		background-color: var(--secondary-dark);
		width: 100%;
	}

	main {
		padding: 0.5rem;
	}
</style>
