<script lang="ts">
	import Card from '$lib/ui/card.svelte';
	import { fly } from 'svelte/transition';
	import { spy } from '$lib/stores/spy-store.svelte';
	import { onMount } from 'svelte';

	onMount(() => {
		spy.update(items => {
			for (const key in items) {
				items[key] = key === 'isProjectsActive' ? true : false;
			}
			return Object.assign(items);
		});
	});
</script>

<section
	class="section"
	in:fly={{ delay: 200, duration: 300, x: -window.innerWidth }}
	out:fly={{ duration: 400, x: window.innerWidth }}
>
	<h1>Some section</h1>
	<div class="grid">
		<Card />
		<Card />
		<Card />
	</div>
</section>

<style lang="scss">
	section {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		z-index: 10;
	}

	.grid {
		width: 100%;
		padding: 1rem;
		display: grid;
		grid-template-rows: auto;
		grid-template-columns: 1fr;
		gap: 1rem;
	}

	@media (min-width: 62rem) {
		.grid {
			grid-template-columns: repeat(3, 1fr);
		}
	}
</style>
