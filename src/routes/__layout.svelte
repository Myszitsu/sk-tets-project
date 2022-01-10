<script lang="ts">
	import '../styles/global.scss';
	import Nav from '$lib/ui/nav.svelte';
	import { onMount } from 'svelte';

	onMount(() => {
		setContainerSize()
	});

	function setContainerSize(event? : Event) {
		const svelteContainer = window.document.getElementById('svelte');
		svelteContainer.style.minHeight = `${window.innerHeight}px`;
	}
</script>

<svelte:window on:resize="{setContainerSize}"/>
<Nav />
<main class="main">
	<slot />
</main>

<style lang="scss">
</style>
