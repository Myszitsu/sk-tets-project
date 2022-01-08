<script lang="ts">

</script>

<div class="card">
   <slot></slot>
</div>

<style lang="scss">
   .card {
      grid-column: span 1;
      display: flex;
      align-items: center;
      flex-direction: column;
      padding-bottom: 1rem;
      width: 100%;
      background-color: #FFDCCC;
      border: 2px solid var(--main-bg-color);
   }
</style>