<script lang="ts">
   import { spy } from "$lib/stores/spy-store.svelte";
</script>

<nav>
	<ul>
		<li class:spy={$spy.isHomeActive}><a href="/"><i class="fas fa-home" /></a></li>
		<li class:spy={$spy.isAboutActive}>
			<a href="/about"><i class="fas fa-info-circle" /></a>
		</li>
		<li class:spy={$spy.isProjectsActive}>
			<a href="/projects"><i class="fas fa-project-diagram" /></a>
		</li>
	</ul>
</nav>

<style lang="scss">
	nav {
		position: fixed;
		top: 1rem;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 90vw;
		height: 4rem;
		background-color: var(--secondary-bg-color);
		z-index: 100;
		border: 1px solid var(--main-bg-color);
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
			color: var(--secondary-dark);
			transition: color 0.2s;
         padding: 1rem;

			&:hover {
				color: var(--main-bg-color);
			}
		}
	}

	.spy {
      i{
                  color: var(--main-bg-color);
         border-bottom: 3px solid var(--main-bg-color);

      }
	}
</style>
