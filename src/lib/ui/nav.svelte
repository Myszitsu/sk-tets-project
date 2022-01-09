<script lang="ts">
	import { spy } from '$lib/stores/spy-store.svelte';
	let header: HTMLElement;

	let hasScrolled: boolean;
</script>

<svelte:window
	on:scroll={() =>
		window.scrollY > header.clientHeight
			? (hasScrolled = true)
			: (hasScrolled = false)}
/>
<header bind:this={header} class:strechted={hasScrolled}>
	<nav>
		<ul>
			<li class:spy={$spy.isHomeActive}>
				<a href="/" aria-label="home"><i class="fas fa-home" /></a>
			</li>
			<li class:spy={$spy.isAboutActive}>
				<a href="/about" aria-label="about"><i class="fas fa-info-circle" /></a>
			</li>
			<li class:spy={$spy.isProjectsActive}>
				<a href="/projects" aria-label="projects"
					><i class="fas fa-project-diagram" /></a
				>
			</li>
		</ul>
	</nav>
</header>

<style lang="scss">
	header {
		position: fixed;
		top: 1rem;
		display: flex;
		justify-content: center;
		align-items: center;
		// width: 90vw;
		width: clamp(200px, 90vw, 80rem);
		height: 4rem;
		background-color: var(--secondary-dark);
		z-index: 100;
		border: 2px solid var(--main-bg-color);
		transition: border 0.3s, background-color 0.3s, transform 0.3s, width 0.3s;
	}

	ul {
		list-style-type: none;
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 1rem;
		padding: 0.5rem;
	}

	a {
		text-decoration: none;

		i {
			font-size: 1.4rem;
			color: var(--secondary-bg-color);
			transition: color 0.2s;
			padding: 1rem;

			&:hover {
				color: var(--main-bg-color);
			}
		}
	}
	

	.strechted {
		transform: translateY(-1rem);
		width: 100%;
	}

	// @media (min-width: 80rem) {
	// 	header {
	// 		width: 80rem;
	// 	}
	// }

	.spy {
		i {
			position: relative;
			color: var(--main-bg-color);
			border-bottom: 2px solid var(--main-bg-color);
		}
	}
</style>
