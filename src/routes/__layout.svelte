<script lang="ts">
	import '../styles/global.scss';
	import Nav from '$lib/ui/nav.svelte';
	import { beforeUpdate } from 'svelte';

	beforeUpdate(() => {
		let vh = window.innerHeight * 0.01;
		document.documentElement.style.setProperty('--vh', `${vh}px`);
	})

	function setContainerHeight() {
		let vh = window.innerHeight * 0.01;
		document.documentElement.style.setProperty('--vh', `${vh}px`);
	}
</script>

<svelte:window on:resize="{setContainerHeight}"/>
<Nav />
<main class="main">
	<slot />
</main>

<style lang="scss">
</style>
