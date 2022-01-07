<script lang="ts">
   import '../styles/global.scss'
   import Nav from '$lib/ui/nav.svelte'
   
</script>

<Nav />
<svelte:body style="min-height: ${window.innerHeight}" />
   <main class="main">
      <slot></slot>   
   </main>
