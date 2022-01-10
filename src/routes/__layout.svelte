<script lang="ts">
	import '../styles/global.scss';
	import Nav from '$lib/ui/nav.svelte';
	import { beforeUpdate, onMount } from 'svelte';
	let main: HTMLElement

	beforeUpdate(() => {
		setContainerHeight()
	})

	onMount(() => {
		setContainerHeight()
	})

	function setContainerHeight() {
		const container = document.getElementById('svelte')
		container.style.minHeight = `${window.innerHeight}px`
	}
</script>

<svelte:window on:resize="{setContainerHeight}"/>
<Nav />
<main bind:this={main} class="main">
	<slot />
</main>

<style lang="scss">
</style>
