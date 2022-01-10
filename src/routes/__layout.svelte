<script lang="ts">
	import '../styles/global.scss';
	import Nav from '$lib/ui/nav.svelte';
	import { beforeUpdate, onMount } from 'svelte';
	let main: HTMLElement

	onMount(() => {
		setContainerHeight()
	})

	function setContainerHeight() {
		main.style.minHeight = `${window.innerHeight}px`
	}
</script>

<svelte:window on:resize="{setContainerHeight}"/>
<Nav />
<main bind:this={main} class="main">
	<slot />
</main>

<style lang="scss">
</style>
