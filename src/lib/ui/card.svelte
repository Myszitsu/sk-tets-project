<script lang="ts">

</script>

<div class="card">
   <slot></slot>
</div>

<style lang="scss">
   .card {
      grid-column: span 1;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      padding: 1rem 0;
      width: 100%;
      background-color: #FFDCCC;
      border: 2px solid var(--secondary-bg-color);
   }
</style>