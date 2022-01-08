<script lang="ts">
	import '../styles/global.scss';
	import Nav from '$lib/ui/nav.svelte';
	import { onMount } from 'svelte';

	// min-hegiht set via JS instead of css due to mobile browsers height bug(?)
	onMount(() => {
		const svelteContainer = window.document.getElementById('svelte');
		svelteContainer.style.minHeight = `${window.innerHeight}px`;
	});
</script>

<Nav />
<main class="main">
	<slot />
</main>

<style lang="scss">
</style>
