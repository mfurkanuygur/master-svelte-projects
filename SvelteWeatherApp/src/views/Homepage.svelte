<script>
  import { onMount } from "svelte";
  import Loading from "../lib/Loading.svelte";
  import DisplayLocation from "../lib/DisplayLocation.svelte";
  import EnterForm from "../lib/EnterForm.svelte";
  import { getApiData } from "../request/request";

  let cityName = "Kayseri";
  let cityDatas = undefined;
  const handleSearchCity = async (newCity) => {
    cityName = newCity;
    cityDatas = await getApiData(cityName);
  };

  onMount(async () => {
    cityDatas = await getApiData(cityName);
  });

  $: cityDatas;
</script>

<h1 class="main-title">Weather App with Svelte</h1>
<EnterForm {handleSearchCity} />
{#if cityDatas}
  <DisplayLocation
    citySummaryData={cityDatas[0]}
    cityDetailData={cityDatas[1]}
  />
{:else}
  <Loading />
{/if}

<style>
</style>
