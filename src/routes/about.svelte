<script lang="ts">
	import { fly } from 'svelte/transition';
	import { spy } from '$lib/stores/spy-store.svelte';
	import { onMount } from 'svelte';

	onMount(() => {
		spy.update(items => {
			for (const key in items) {
				items[key] = key === 'isAboutActive' ? true : false;
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
	<h1>Some section</h1>
</section>

<style lang="scss">
	section {
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
