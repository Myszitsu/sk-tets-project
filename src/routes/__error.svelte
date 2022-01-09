<script lang="ts" context="module">
	export function load({ error }) {
		return {
			props: { message: error.message },
		};
	}
</script>

<script>
	import ButtonLink from '$lib/ui/button-link.svelte';

	import { fly } from 'svelte/transition';
	export let message;
</script>

<div
	in:fly={{ delay: 200, duration: 300, x: -window.innerWidth }}
	out:fly={{ duration: 400, x: window.innerWidth }}
	class="error"
>
      <h1>ERROR</h1>
      <p class="message">{message}</p>
      <ButtonLink content={'REDIRECT TO HOME PAGE'} light={true}  href={'/'} />
</div>

<style>

	.message {
      padding: 0.6rem 1rem;
      font-weight: bold;
		color: var(--secondary-dark);
      background-color: var(--secondary-light);
      border-radius: .15rem;
	}
	.error {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 2rem;
		padding: 2rem 4rem;
		width: max-content;
		color: var(--main-bg-color);
		background-color: var(--secondary-dark);
		border: 3px solid var(--main-bg-color);
	}

</style>
