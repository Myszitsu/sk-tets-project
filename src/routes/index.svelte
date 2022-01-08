<script lang="ts">
	import { fly } from 'svelte/transition';
	import { spy } from '$lib/stores/spy-store.svelte';
	import { onMount } from 'svelte';
	import Headline from '$lib/ui/headline.svelte';
	import ButtonLink from '$lib/ui/button-link.svelte';
	import MediaQuery from '$lib/helpers/media-query.svelte';

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
	class="section home"
	in:fly={{ delay: 200, duration: 300, x: -window.innerWidth }}
	out:fly={{ duration: 400, x: window.innerWidth }}
>
	<MediaQuery query="(min-width: 48rem)" let:matches>
		{#if matches}
			<h1 class="h1">HELLO WORLD</h1>
		{/if}</MediaQuery
	>
	<div class="content">
		<MediaQuery query="(max-width: 48rem)" let:matches>
			{#if matches}
				<h1 class="h1">HELLO WORLD</h1>
			{/if}</MediaQuery
		>
		<MediaQuery query="(min-width: 36rem)" let:matches>
			{#if matches}
				<p>
					I’m an amateur web developer looking for an oportunity to start a
					professional career. Below you will find a few bits about me.
				</p>
			{/if}
		</MediaQuery>
		<MediaQuery query="(max-width: 48rem)" let:matches>
			{#if matches}
			<ul>
				<li>
					<ButtonLink
						width={'100%'}
						light={true}
						content={'ABOUT'}
						href="/about"
					/>
				</li>
				<li>
					<ButtonLink
						width={'100%'}
						light={true}
						content={'PROJECTS'}
						href="/projects"
					/>
				</li>
			</ul>
			{/if}</MediaQuery
		>
		<MediaQuery query="(min-width: 48rem)" let:matches>
			{#if matches}
			<p>I've taken multiple courses and have been learning frontend technologies since April 2021. I am eager to learn from anyone that is willing to teach and hopeful to go commercial in the forseeable future.</p>
			<ul>
				<li>
					<ButtonLink
						width={'100%'}
						content={'ABOUT'}
						href="/about"
					/>
				</li>
				<li>
					<ButtonLink
						width={'100%'}
						content={'PROJECTS'}
						href="/projects"
					/>
				</li>
			</ul>
			{/if}</MediaQuery
		>
	</div>
	<img src="portrait-svelte.png" alt="" />
</section>

<style lang="scss">
	.home {
		display: grid;
		grid-template-rows: min-content 1fr;
		grid-template-areas:
			'info'
			'img';
		color: var(--main-bg-color);
		background-color: var(--secondary-light);
		border: 2px solid var(--main-bg-color);

		.content {
			grid-area: info;
			display: flex;
			justify-content: center;
			flex-direction: column;
			align-items: center;
			padding-block: 1rem;
			color: var(--main-bg-color);
			background-color: var(--secondary-dark);

			p {
				margin: 1rem 1rem;
				padding-inline: 1rem;
				line-height: 1.4;
			}

			ul {
				list-style-type: none;
				display: flex;
				padding-block: 0.5rem;
				justify-content: center;
				flex-wrap: wrap;
				gap: 1rem;
				width: 85%;
				li {
					flex-grow: 1;
				}
			}
		}

		.h1 {
			padding-inline: 1rem;
			font-family: 'Monoton', serif;
			font-size: 32px;
			font-weight: 400;
			letter-spacing: 0.1rem;
		}

		img {
			grid-area: img;
			padding: 32px;
			justify-self: center;
			align-self: center;
			width: 100%;
			object-fit: scale-down;
		}
	}

	@media (min-width: 36rem) {
		.h1 {
			font-size: 2rem;
		}
	}
	@media (min-width: 48rem) {
		.home {
			grid-template-rows: min-content 1fr;
			grid-template-columns: repeat(2, 1fr);
			grid-template-areas:
				'h1 h1'
				'img info';
			.content {
				position: relative;
				align-self: center;
				height: 100%;
				color: black;
				justify-content: space-evenly;
				background-color: transparent;
				p {
					grid-area: info;
				}

				&::before {
					content: '';
					position: absolute;
					width: .2rem;
					height: 90%;
					left: 0;
					top: 50%;
					transform: translateY(-50%);
					background-color: var(--secondary-dark);
				}
			}
		}
		.h1 {
			text-align: center;
			padding-block: 1rem;
			background-color: var(--secondary-dark);
			grid-area: h1;
		}
	}

	@media (min-width: 62rem) {
		.home {
			.content {
				p {
					 font-size: 1.4rem;
				}
			}
			img {
			padding: 2.5rem;
			width: 80%;
		}
		}		
	}
</style>
