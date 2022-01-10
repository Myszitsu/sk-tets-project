<script lang="ts">
	import { onMount } from 'svelte';
	import { SnakeGame } from '$lib/projects/snake.svelte';
	import MediaQuery from '$lib/helpers/media-query.svelte';
	import { fly } from 'svelte/transition';
	let frame: HTMLDivElement;
	let game: SnakeGame;

	onMount(() => {
		game = new SnakeGame(frame);
		game.movement.movementSpeed = 60;
	});

	function movementHandler(event: KeyboardEvent | Event) {
		if (
			event instanceof KeyboardEvent &&
			event.key.includes('Arrow') &&
			game.movement.isMovementFinished &&
			(event.key !== game.movement.eventIdentifier || game.movement.isPaused)
		) {
			game.movement.isMovementFinished = false;
			game.movement.movementHandler(event);
		}
		if (
			event.target instanceof HTMLButtonElement &&
			event.target.dataset.event &&
			game.movement.isMovementFinished &&
			(event.target.dataset.event !== game.movement.eventIdentifier ||
				game.movement.isPaused)
		) {
			game.movement.isMovementFinished = false;
			game.movement.movementHandler(event);
		}
	}

	function resizeSnake() {
		game.frame.setSize();
		game.movement.resetGame();
	}
</script>

<svelte:head>
	<title>Snake</title>
</svelte:head>
<svelte:window on:resize={resizeSnake} on:keydown={movementHandler} />
<section
	in:fly={{ delay: 200, duration: 300, x: -window.innerWidth }}
	out:fly={{ duration: 400, x: window.innerWidth }}
	class="section section--snake"
>
	<header>
		<button
			on:click={() => {
				if (game.movement.isMovementFinished) {
					game.movement.isMovementFinished = false;
					game.movement.play();
				}
			}}><i class="fas fa-play" /></button
		>
		<button
			on:click={() => {
				game.movement.isMovementFinished = true;
				game.movement.pause();
			}}><i class="fas fa-pause" /></button
		>
		<button
			on:click={() => {
				game.movement.resetGame();
			}}><i class="fas fa-redo" /></button
		>
	</header>
	<main>
		<div bind:this={frame} class="frame">
			<h2 id="h2">APPLES: 0</h2>
			<div id="apple" />
			<div id="head" />
		</div>
	</main>
	<footer>
		<div class="controls controls--left">
			<button
				on:click={movementHandler}
				class="arrow arrow--left"
				data-event="ArrowLeft"
				aria-label="Arrow Left"><i class="fas fa-arrow-left" /></button
			>
			<button
				on:click={movementHandler}
				class="arrow arrow--down"
				data-event="ArrowDown"
				aria-label="Arrow Down"><i class="fas fa-arrow-down" /></button
			>
		</div>
		<MediaQuery query="(min-width: 40rem)" let:matches>
			{#if matches}
				<p class="info">NAVIGATE WITH ARROW KEYS OR BUTTONS</p>
			{/if}
		</MediaQuery>
		<div class="controls controls--right">
			<button
				on:click={movementHandler}
				class="arrow arrow--up"
				data-event="ArrowUp"
				aria-label="Arrow Up"><i class="fas fa-arrow-up" /></button
			>
			<button
				on:click={movementHandler}
				class="arrow arrow--right"
				data-event="ArrowRight"
				aria-label="Arrow Right"><i class="fas fa-arrow-right" /></button
			>
		</div>
	</footer>
</section>

<style lang="scss">
	.section--snake {
		display: grid;
		align-content: start;
		grid-template-rows: min-content auto 1fr;
		color: var(--main-bg-color);
		background-color: var(--secondary-dark);
		border: 2px solid var(--main-bg-color);
	}

	header {
		display: flex;
		justify-content: center;
		align-items: center;
		padding-block: 20px;
		height: 100%;
		gap: 10vw;

		button {
			width: clamp(20px, 15vw, 30px);
			aspect-ratio: 1 / 1;
			border: none;
			background-color: transparent;

			i {
				font-size: clamp(15px, 8vw, 30px);
			}
		}
	}

	main {
		display: grid;
		place-items: center;
		height: 50vh;
		width: 100%;
	}

	footer {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100%;
		gap: 3vw;
		padding: 1vw;

		.controls {
			width: 50%;
			display: flex;
			justify-content: center;
			align-self: center;
			gap: 3vw;

			&--left {
				justify-content: flex-end;
			}

			&--right {
				justify-content: flex-start;
			}

			.arrow {
				width: clamp(20px, 40%, 70px);
				aspect-ratio: 1 / 1;
				background-color: var(--secondary-dark);
				border: 3px solid var(--main-bg-color);
				border-radius: 5%;
				i {
					font-size: clamp(15px, 10vw, 45px);
				}
			}
		}
	}

	i {
		pointer-events: none;
		color: var(--main-bg-color);
	}

	h2 {
		margin-top: 20px;
		text-align: center;
		color: var(--secondary-light);
	}

	button {
		cursor: pointer;
	}

	@media (min-width: 40rem) {
		.info {
			text-align: center;
			font-size: clamp(20px, 4vw, 32px);
			font-weight: 400;
			letter-spacing: 0.1rem;
		}

		footer {
			justify-content: space-between;
			.controls {
				width: 20%;
				flex-direction: column;
				gap: 5px;

				&--left {
					align-items: flex-start;
				}

				&--right {
					align-items: flex-end;
				}
				.arrow {
					width: clamp(20px, 80%, 70px);
				}
			}
		}
	}
</style>
