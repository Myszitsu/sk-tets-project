<script lang="ts">
	import '../styles/global.scss';
	import Nav from '$lib/ui/nav.svelte';
	import { beforeUpdate, onMount } from 'svelte';
	let main: HTMLElement

	onMount(() => {
		setContainerSize()
	});

	function setContainerSize() {
		main.style.minHeight = `${window.innerHeight}px`;
	}
</script>

<svelte:window on:resize="{setContainerSize}"/>
<Nav />
<main bind:this={main} class="main">
	<slot />
</main>

<style lang="scss">
</style>
