<script lang="ts">
	import ProjectGrid from '$lib/ui/project-grid.svelte';
	import { fly } from 'svelte/transition';
	import { spy } from '$lib/stores/spy-store.svelte';
	import { onMount } from 'svelte';
import H1 from '$lib/ui/h1.svelte';

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
	<H1 title={"MY PROJECTS"}/>
	<main class="grid">
		<ProjectGrid />
		<ProjectGrid />
		<ProjectGrid />
		<ProjectGrid />
	</main>
</section>

<style lang="scss">
	section {
		display: flex;
		align-items: center;
		flex-direction: column;
	}

	.grid {
		width: 100%;
		padding-inline: .7rem;
      margin-top: .5rem;
      margin-bottom: 1.5rem;
		display: grid;
		grid-template-rows: auto;
		grid-template-columns: 1fr;
		gap: 1.4rem;
	}

	@media (min-width: 48rem) {
		.grid {
			grid-template-columns: repeat(2, 1fr);
         padding-inline: 1.5rem;
		}
	}
	// @media (min-width: 62rem) {
	// 	.grid {
	// 		grid-template-columns: repeat(3, 1fr);
	// 	}
	// }
	@media (min-width: 70rem) {
		.grid {
			grid-template-columns: repeat(3, 1fr);
		}
	}
</style>
