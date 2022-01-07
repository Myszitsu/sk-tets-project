<script lang="ts">
import Card from "./card.svelte";


</script>
<Card>
   <header>
      <h2>Project Title</h2>
      <img src="https://cdn.pixabay.com/photo/2020/06/28/05/30/jesus-5347929_960_720.jpg" alt="snake graphic">
   </header>
   <main>
      <div class="description">
         <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas quae quam vel laudantium id repellendus adipisci ipsum! Voluptates illo eos delectus debitis quam totam explicabo voluptatem. Accusamus ipsam error fugiat.</p>
      </div>
   </main>
   <footer>
      <a href="/">OPEN</a>
   </footer>
</Card>

<style lang="scss">
   img {
         width: 100%;
      }

      header {
         text-align: center;

         h2 {
            padding: 0.5rem;
            padding-bottom: 1rem;
         }
      }

      main {
         padding: .5rem;

         p {
            margin: 1rem 1rem .5rem;
         }
      }

      footer {
         display: flex;
         justify-content: flex-start;
         margin-block: .5rem;
         padding-inline: 1.5rem;
         width: 100%;

         a {
            display: inline-block;
            padding: 0.6rem 1.2rem;
            font-weight: bold;
            color: var(--main-bg-color);
            background-color: var(--secondary-bg-color);
            text-decoration: none;
            border-radius: .3rem;
            text-align: center;
         }
      }
</style>
