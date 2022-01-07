<script lang="ts">
	import { fly } from 'svelte/transition';
	import { spy } from '$lib/stores/spy-store.svelte';
	import { onMount } from 'svelte';
import H1 from '$lib/ui/h1.svelte';

	onMount(() => {
		spy.update(items => {
			for (const key in items) {
				items[key] = key === 'isHomeActive' ? true : false;
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
	<H1 title={"HOME"} />
</section>

<style lang="scss">
	section {
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
