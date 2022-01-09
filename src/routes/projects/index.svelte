<script lang="ts">
	import ProjectGrid from '$lib/ui/project-grid-card.svelte';
	import { fly } from 'svelte/transition';
	import { spy } from '$lib/stores/spy-store.svelte';
	import Headline from '$lib/ui/headline.svelte';
	import { onDestroy, onMount } from 'svelte';

onDestroy(() => {
		spy.update(items => {
			for (const key in items) {
				items[key] = false;
			}
			return Object.assign(items);
		});
	})	

	onMount(() => {
		spy.update(items => {
			for (const key in items) {
				items[key] = key === 'isProjectsActive' ? true : false;
			}
			return Object.assign(items);
		});
	});

	
</script>

<svelte:head>
   <title>Projects</title>
</svelte:head>
<section
	class="section s"
	in:fly={{ delay: 200, duration: 300, x: -window.innerWidth }}
	out:fly={{ duration: 400, x: window.innerWidth }}
>
	<Headline title={'MY PROJECTS'} />
	<main class="grid">
		<ProjectGrid title={'Snake'} imgAlt={'snake ilustration'} href={'/projects/snake'} githubHref={'https://github.com/Myszitsu/snake-typescript-oop'} imgURL='https://cdn.pixabay.com/photo/2020/06/28/05/30/jesus-5347929_960_720.jpg'>
			This is a snake minigame written in TypeScript with Class structure. The component is scalable and can use either arrows keys or buttons to navigate. Follow the link below for it's own GitHub's repository.
		</ProjectGrid>
		<ProjectGrid />
		<ProjectGrid />
		<ProjectGrid />
	</main>
</section>

<style lang="scss">
	.s {
		border: none;
		background: transparent;
	}

	.grid {
		width: 100%;
		// padding-inline: .5rem;
		margin-top: 0.5rem;
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
