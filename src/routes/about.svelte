<script lang="ts">
	import { fly } from 'svelte/transition';
	import { spy } from '$lib/stores/spy-store.svelte';
	import { onMount } from 'svelte';
	import Headline from '$lib/ui/headline.svelte';
	import AboutCard from '$lib/ui/about-card.svelte';

	onMount(() => {
		spy.update(items => {
			for (const key in items) {
				items[key] = key === 'isAboutActive' ? true : false;
			}
			return Object.assign(items);
		});
	});
</script>

<svelte:head>
   <title>About</title>
</svelte:head>
<section
	class="section"
	in:fly={{ delay: 200, duration: 300, x: -window.innerWidth }}
	out:fly={{ duration: 400, x: window.innerWidth }}
>
	<Headline title={'ABOUT'} />
	<div class="grid">
		<AboutCard title={'SOLID BASICS'}>
			<div class="graphics">
				<svg
				aria-label="svelte"
					class="main-svg"
					xmlns="http://www.w3.org/2000/svg"
					width="107"
					height="128"
					viewBox="0 0 107 128"
					><title>svelte-logo</title><path
						d="M94.1566,22.8189c-10.4-14.8851-30.94-19.2971-45.7914-9.8348L22.2825,29.6078A29.9234,29.9234,0,0,0,8.7639,49.6506a31.5136,31.5136,0,0,0,3.1076,20.2318A30.0061,30.0061,0,0,0,7.3953,81.0653a31.8886,31.8886,0,0,0,5.4473,24.1157c10.4022,14.8865,30.9423,19.2966,45.7914,9.8348L84.7167,98.3921A29.9177,29.9177,0,0,0,98.2353,78.3493,31.5263,31.5263,0,0,0,95.13,58.117a30,30,0,0,0,4.4743-11.1824,31.88,31.88,0,0,0-5.4473-24.1157"
						style="fill:currentColor"
					/><path
						d="M45.8171,106.5815A20.7182,20.7182,0,0,1,23.58,98.3389a19.1739,19.1739,0,0,1-3.2766-14.5025,18.1886,18.1886,0,0,1,.6233-2.4357l.4912-1.4978,1.3363.9815a33.6443,33.6443,0,0,0,10.203,5.0978l.9694.2941-.0893.9675a5.8474,5.8474,0,0,0,1.052,3.8781,6.2389,6.2389,0,0,0,6.6952,2.485,5.7449,5.7449,0,0,0,1.6021-.7041L69.27,76.281a5.4306,5.4306,0,0,0,2.4506-3.631,5.7948,5.7948,0,0,0-.9875-4.3712,6.2436,6.2436,0,0,0-6.6978-2.4864,5.7427,5.7427,0,0,0-1.6.7036l-9.9532,6.3449a19.0329,19.0329,0,0,1-5.2965,2.3259,20.7181,20.7181,0,0,1-22.2368-8.2427,19.1725,19.1725,0,0,1-3.2766-14.5024,17.9885,17.9885,0,0,1,8.13-12.0513L55.8833,23.7472a19.0038,19.0038,0,0,1,5.3-2.3287A20.7182,20.7182,0,0,1,83.42,29.6611a19.1739,19.1739,0,0,1,3.2766,14.5025,18.4,18.4,0,0,1-.6233,2.4357l-.4912,1.4978-1.3356-.98a33.6175,33.6175,0,0,0-10.2037-5.1l-.9694-.2942.0893-.9675a5.8588,5.8588,0,0,0-1.052-3.878,6.2389,6.2389,0,0,0-6.6952-2.485,5.7449,5.7449,0,0,0-1.6021.7041L37.73,51.719a5.4218,5.4218,0,0,0-2.4487,3.63,5.7862,5.7862,0,0,0,.9856,4.3717,6.2437,6.2437,0,0,0,6.6978,2.4864,5.7652,5.7652,0,0,0,1.602-.7041l9.9519-6.3425a18.978,18.978,0,0,1,5.2959-2.3278,20.7181,20.7181,0,0,1,22.2368,8.2427,19.1725,19.1725,0,0,1,3.2766,14.5024,17.9977,17.9977,0,0,1-8.13,12.0532L51.1167,104.2528a19.0038,19.0038,0,0,1-5.3,2.3287"
						style="fill:#a43439"
					/></svg
				>
				<div class="icons">
					<i class="fab fa-html5" aria-label="html5" />
					<i class="fab fa-css3-alt" aria-label="css3" />
					<svg class="typescript"
					aria-label="typescript"
						xmlns="http://www.w3.org/2000/svg"
						width="400px"
						height="400px"
						viewBox="0 0 400 400"
						id="Layer_1"
						><style>
							.st0 {
								fill: currentColor;
							}
							.st1 {
								fill: #a43439;
							}
						</style><path class="st0" d="M0 200V0h400v400H0" /><path
							class="st1"
							d="M87.7 200.7V217h52v148h36.9V217h52v-16c0-9 0-16.3-.4-16.5 0-.3-31.7-.4-70.2-.4l-70 .3v16.4l-.3-.1zM321.4 184c10.2 2.4 18 7 25 14.3 3.7 4 9.2 11 9.6 12.8 0 .6-17.3 12.3-27.8 18.8-.4.3-2-1.4-3.6-4-5.2-7.4-10.5-10.6-18.8-11.2-12-.8-20 5.5-20 16 0 3.2.6 5 1.8 7.6 2.7 5.5 7.7 8.8 23.2 15.6 28.6 12.3 41 20.4 48.5 32 8.5 13 10.4 33.4 4.7 48.7-6.4 16.7-22 28-44.3 31.7-7 1.2-23 1-30.5-.3-16-3-31.3-11-40.7-21.3-3.7-4-10.8-14.7-10.4-15.4l3.8-2.4 15-8.7 11.3-6.6 2.6 3.5c3.3 5.2 10.7 12.2 15 14.6 13 6.7 30.4 5.8 39-2 3.7-3.4 5.3-7 5.3-12 0-4.6-.7-6.7-3-10.2-3.2-4.4-9.6-8-27.6-16-20.7-8.8-29.5-14.4-37.7-23-4.7-5.2-9-13.3-11-20-1.5-5.8-2-20-.6-25.7 4.3-20 19.4-34 41-38 7-1.4 23.5-.8 30.4 1l-.2.2z"
						/></svg
					>
				</div>
			</div>
			<main slot="main">
				<p>
					I have good understanding of the basics of HTML5, CSS3, JavaScript &
					TypeScript, with some more advanced concepts like testing or Web Components on the way. By learning Svelte I absorbed the concepts of component-base approach to building websites, routing and stores/services.
				</p>
				<p>
					Currently I'm exploring Angular to get better understading of how to build complex applications and work with API & backend data more efficiently, but Vue, React and Node.js are on my target as well.
				</p>
			</main>
		</AboutCard>
		<AboutCard title={'FAMILIAR WITH'}>
			<div class="graphics">
				<svg
				aria-label="webpack"
					class="main-svg"
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 32 32"
					width="64"
					height="64"
					><path
						d="M29.54 24.663L16.57 32v-5.713l8.08-4.446zm.888-.803V8.52l-4.744 2.742v9.862zm-27.966.803L15.43 32v-5.713L7.345 21.84zm-.888-.803V8.52l4.744 2.742v9.862zM2.13 7.524L15.43 0v5.522L6.84 10.25zm27.74 0L16.57 0v5.522l8.59 4.723z"
						fill="#fff9eb"
					/><path
						d="M15.43 25.237L7.456 20.85v-8.684l7.974 4.604zm1.14 0l7.975-4.383v-8.69L16.57 16.77zm-.57-8.8zm-8.004-5.275L16 6.763l8.004 4.4L16 15.783z"
						fill="currentColor"
					/></svg
				>
				<div class="icons">
					<i class="fab fa-figma" aria-label="figma" />
					<i class="fab fa-git-alt" aria-label="git" />
					<a href="https://github.com/Myszitsu" target="__blank" aria-label="github link"><i class="fab fa-github" /></a>
				</div>
			</div>
			<main slot="main">
				<p>
					I have some experience with module bundlers like Webpack 5+, rollup 3+
					& gulp 4. When constructing a barebone project, Webpack would be my
					bundler of choice.
				</p>

				<p>
					I used Figma for simple designs, occasionally work with git and
					GitHub. Recently I adopted Firebase 9 with collection management and
					basics of user authentication.
				</p>
			</main>
		</AboutCard>
		<AboutCard title={'MY EXPERIENCE'}>
			<div class="graphics">
				<i class="fas fa-landmark" aria-label="greece" />
				<div class="icons">
					<i class="fas fa-comments-dollar" aria-label="product management" />
					<i class="fas fa-headset" aria-label="communication"/>
					<i class="fas fa-table" aria-label="excel" />
				</div>
			</div>
			<main slot="main">
				<p>
					My latest job position was Assistant Product Manager at a Tour Operator
					company that contracts trips to Greece nad Cyprus. It was a true
					rollercoster, but I had an opportunity to work with many departments,
					including cooperation with IT department due to deployment of new
					reservation system. That's when my intrest with Information Technology
					started.
				</p>
				<p>
					Previously I worked in the same company as Senior B2B and B2C
					consultant.
				</p>
			</main>
		</AboutCard>
		<AboutCard title={"THIS WEBSITE"}>
			<div class="graphics">
				<i class="fas fa-tools" aria-label="under construction"></i>
				<div class="icons web">
					<a href="/projects" aria-label="projects"><i class="fas fa-folder-open"></i></a>
					<a href="https://codepen.io/Myszitsu/" target="__blank" aria-label="codpen profile"><i class="fab fa-codepen"></i></a>
					<a href="https://github.com/Myszitsu/sk-tets-project" target="__blank" aria-label="github-link"><i class="fab fa-github" /></a>
				</div>
			</div>
			<main slot="main">
				<p>Keep in mind that this website is under construction. It was built with SvelteKit and deployed via Vercel.</p>
				<p>You can visit this particular repository by clicking GitHub icon on this card. Commits are not regular nor very descriptive since I was eager to deploy this website in under 3 days. I will do my best to be more attentive with future changes. </p>
				<p>Check out my Codepen profile by clicking the icon.</p>
			</main>
		</AboutCard>
	</div>
</section>

<style lang="scss">
	.grid {
		width: 100%;
		min-height: 70vh;
		margin-top: 0.5rem;
		margin-bottom: 1.5rem;
		display: grid;
		grid-template-rows: auto;
		grid-template-columns: 1fr;
		justify-content: center;
		gap: 1.4rem;
	}

	.graphics {
		color: var(--secondary-bg-color);

		.main-svg {
			margin-top: 0.5rem;
			height: 6rem;
		}
		.icons {
			display: flex;
			justify-content: center;
			gap: 3rem;
			margin-block: 1.5rem;

			svg {
				height: 2.4rem;
				width: 2.4rem;
			}

			i {
				font-size: 2.5rem;
			}

			.fa-github {
				transition: color 0.3s, transform 0.3s;

				&:hover {
					transform: scale(1.1);
					color: var(--main-bg-color);
				}
			}

			.typescript {
				border-radius: .3rem;
			}

			a {
				text-decoration: none;
				color: var(--link-icon);
			}
		}

		.icons.web {
			i {
				transition: color 0.3s, transform 0.3s;

				&:hover {
					transform: scale(1.1);
					color: var(--main-bg-color);
				}
			}
		}

		.fa-landmark, .fa-tools {
			font-size: 5rem;
			margin-block: .863rem;
		}
	}

	main {
		p {
			padding: 1rem;
		}
	}

	@media (min-width: 48rem) {
		.grid {
			grid-template-columns: repeat(2, 1fr);
		}
	}
	@media (min-width: 70rem) {
		.grid {
			grid-template-columns: repeat(3, 1fr);
		}
	}
</style>
