<script lang="ts">
	import '../styles/global.scss';
	import { onMount } from 'svelte';
import Nav from '$lib/UI/nav.svelte';

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
