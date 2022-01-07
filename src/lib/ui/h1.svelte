<script lang="ts">
   export let title: string;
</script>


<h1>{title}</h1>

<style lang="scss">
   h1 {
      position: relative;
      margin-block: 1.5rem;
      font-weight: bold;
      color: var(--secondary-bg-color);

      &::before {
         position: absolute;
         content: '';
         width: 100%;
         height: .1rem;
         background-color: var(--secondary-bg-color);
         bottom: -.5rem;
      }

   }
</style>