<script lang="ts">

</script>

<div class="card">
<header>
   <h2>Project Title</h2>
   <img src="https://cdn.pixabay.com/photo/2020/06/28/05/30/jesus-5347929_960_720.jpg" alt="snake graphic">
   <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
</header>
<main>
   <div class="description">
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas quae quam vel laudantium id repellendus adipisci ipsum! Voluptates illo eos delectus debitis quam totam explicabo voluptatem. Accusamus ipsam error fugiat.</p>
   </div>
</main>
<footer>
   <a href="/">Play</a>
</footer>
</div>

<style lang="scss">
   .card {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      padding: 1rem 0;
      width: 100%;
      background-color: cyan;
      grid-column: span 1;

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
      }

      a {
         color: var(--main-bg-color);
         text-decoration: none;
         padding: 0.5rem 1rem;
         background-color: var(--secondary-bg-color);
      }
   }
</style>