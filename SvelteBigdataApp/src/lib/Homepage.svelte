<script>
  import { onMount } from "svelte";
  import { getAllProducts } from "../request/request";
  import Loading from "./Loading.svelte";
  import RenderProduct from "./RenderProduct.svelte";

  let products = [];
  let skip = 0;
  let loading = false;
  const fetchProducts = async () => {
    loading = true;
    const data = await getAllProducts(skip);
    products = [...products, ...data];
    loading = false;
  };
  onMount(fetchProducts);

  const handleClick = () => {
    skip += 8;
    fetchProducts();
  };
</script>

<div class="homepage">
  {#if products.length > 0}
  <div>
      <div class="container">
          {#each products as product (product.id)}
              <RenderProduct {product} />
          {/each}
      </div>
      <div class="see-more-container">
          {#if loading}
              <Loading />
          {:else}
              <button class="see-more-button" on:click={handleClick}>See more</button>
          {/if}
      </div>
  </div>
{:else}
  <Loading />
{/if}
</div>
