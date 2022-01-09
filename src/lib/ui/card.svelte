<script lang="ts">

</script>

<div class="card">
   <slot></slot>
</div>

<style lang="scss">
   .card {
      grid-column: span 1;
      position: relative;
      display: flex;
      align-items: center;
      flex-direction: column;
      padding-bottom: 1rem;
      width: 100%;
      background-color: var(--secondary-light);
      border: 2px solid var(--main-bg-color);      
   }

   @media (min-width: 70rem) {
      .card:last-child:nth-child(3n-2) {
         grid-column: 2/3;
      }
   }
</style>