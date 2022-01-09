<script lang="ts">
	export let href: string;
	export let content: string;
	export let blank: boolean = false;
	export let light: boolean = false;
	export let outline: boolean = false;
   export let width: string | undefined = undefined;
</script>

{#if blank}
	<a style="width: {width ?? 'auto'}" class:outline={outline} class:light={light} {href} target="__blank">{content}</a>
{:else}
	<a style="width: {width ?? 'auto'}" class:outline={outline} class:light={light} {href}>{content}</a>
{/if}

<style lang="scss">
	a {
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 0.7rem 1.2rem;
		font-weight: bold;
		color: var(--main-bg-color);
		background-color: var(--secondary-dark);
		text-decoration: none;
		border-radius: 0.3rem;
		text-align: center;
		transition: transform 0.3s, background-color 0.3s;

		&:hover {
			background-color: #d64045;
		}
	}

	.light {
      border: .13rem solid var(--main-bg-color);
		background-color: transparent;
	}

	.outline {
		border: .13rem solid var(--secondary-dark);
		color: var(--secondary-dark);
		background-color: transparent;
		&:hover {
			background-color: rgba(214, 64, 69, .15);
		}
	}
</style>
