<script lang="ts">
	import ProjectGrid from '$lib/ui/project-grid-card.svelte';
   import { fly } from 'svelte/transition';
	import { spy } from '$lib/stores/spy-store.svelte';
	import { onMount } from 'svelte';
import Headline from '$lib/ui/headline.svelte';

	onMount(() => {
		spy.update(items => {
			for (const key in items) {
				items[key] = key === 'isProjectsActive' ? true : false;
			}
			return Object.assign(items);
		});
	});
</script>

<section class="section s" in:fly={{ delay: 200, duration: 300, x: -window.innerWidth }}
            out:fly={{ duration: 400, x: window.innerWidth }}>
	<Headline title={"MY PROJECTS"}/>
	<main class="grid">
		<ProjectGrid />
		<ProjectGrid />
		<ProjectGrid />
		<ProjectGrid />
	</main>
</section>

<style lang="scss">
	.s {
      border: none;
      background:transparent;
   }

	.grid {
		width: 100%;
		// padding-inline: .5rem;
      margin-top: .5rem;
      margin-block: 1.5rem;
		display: grid;
		grid-template-rows: auto;
		grid-template-columns: 1fr;
		gap: 1.4rem;
	}

	@media (min-width: 48rem) {
		.grid {
			grid-template-columns: repeat(2, 1fr);
		}
	}
	@media (min-width: 70rem) {
		.grid {
			grid-template-columns: repeat(3, 1fr);
		}
	}
</style>
