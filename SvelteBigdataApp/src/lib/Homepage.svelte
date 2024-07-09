<script>
    import { onMount } from 'svelte';
    import { getAllProducts } from '../request/request';
    import Loading from './Loading.svelte';
    import RenderProduct from './RenderProduct.svelte';
  
    let products = null;
    let count = 10;
  
    onMount(async () => {
      const data = await getAllProducts();
      products = data;
    });
  
    function handleClick() {
      count += 10;
      console.log(count);
    }
  </script>
  
  <div class="homepage">
    {#if products}
      <div class="container">
        {#each products.slice(0, count) as product (product.id)}
          <RenderProduct {product} />
        {/each}
      </div>
      <div class="see-more-container">
        <button class="see-more-button" on:click={handleClick}>see more</button>
      </div>
    {:else}
      <Loading />
    {/if}
  </div>