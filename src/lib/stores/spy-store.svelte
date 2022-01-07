<script lang="ts" context="module">
   import { writable } from 'svelte/store';

   export const spy = writable({
      isHomeActive: false,
      isAboutActive: false,
      isProjectsActive: false,
   })
</script>