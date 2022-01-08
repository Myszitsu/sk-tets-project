<script lang="ts">
   export let title: string;
   export let headlineType: 'h1' | 'h2' | 'h3' = 'h1';
   export let mode: 'light' | 'dark' = 'light';
</script>

{#if headlineType === 'h1'}
<h1 class="headline" class:light={mode === 'light'}>{title}</h1>
{:else if headlineType === 'h2'}
<h2 class="headline" class:light={mode === 'light'}>{title}</h2>
{:else}
<h3 class="headline">{title}</h3>
{/if}


<style lang="scss">
   .headline {
      position: relative;
      margin: 1.5rem auto;
      font-weight: bold;
      color: var(--secondary-bg-color);
      width: fit-content;

      &::before {
         position: absolute;
         content: '';
         width: 100%;
         height: .1rem;
         background-color: var(--secondary-bg-color);
         bottom: -.5rem;
      }

   }

   .light {
      color: var(--main-bg-color);

      &::before {
         background-color: var(--main-bg-color);
      }
   }
</style>