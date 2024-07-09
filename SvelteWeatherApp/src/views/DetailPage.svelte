<script>
  import { onMount, afterUpdate } from "svelte";
  import { dailyWeathers, remainingDays } from "../chunked/chunked.js";
  import OneDayDetail from "../lib/OneDayDetail.svelte";
  import DailyDetail from "../lib/DailyDetail.svelte";
  import Loading from "../lib/Loading.svelte";

  export let cityDetailData;

  let dailyWeathersData = null;
  let remainingDaysData = null;

  const updateWeatherData = () => {
    if (cityDetailData) {
      dailyWeathersData = dailyWeathers(cityDetailData)[0];
      remainingDaysData = remainingDays(cityDetailData);
    }
  };

  onMount(updateWeatherData);

  afterUpdate(() => {
    updateWeatherData();
  });
</script>

<div class="detail-section">
  <h1 class="detail-title">Today's Weather</h1>
  {#if dailyWeathersData && remainingDaysData}
    <div class="detail-container">
      <div class="today-container">
        {#each dailyWeathersData as weather, index (index)}
          <OneDayDetail {weather} />
        {/each}
      </div>
      <div class="remain-container">
        {#each remainingDaysData as weather, index (index)}
          <DailyDetail {weather} />
        {/each}
      </div>
    </div>
  {:else}
    <Loading />
  {/if}
</div>
