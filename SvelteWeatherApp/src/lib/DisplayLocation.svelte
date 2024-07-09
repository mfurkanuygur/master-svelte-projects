<script>
  import DetailPage from "../views/DetailPage.svelte";
  import feelslike from "../assets/feelslike.png";
  import humidity from "../assets/humidity.png";
  import mintemp from "../assets/mintemp.png";
  import maxtemp from "../assets/maxtemp.png";

  export let citySummaryData;
  export let cityDetailData;

</script>

<div class="container">
  <div class="main-summary">
    <div class="city-summary">
      <div class="card-title">
        <img
          class="weather-img"
          src={`https://openweathermap.org/img/wn/${citySummaryData?.weather[0].icon}@2x.png`}
          alt=""
        />
        <p class="weather-description">
          {citySummaryData?.weather[0].description}
        </p>
      </div>
      <h1>{citySummaryData?.name}</h1>
      <p>Chance of rain: {citySummaryData?.main?.humidity}%</p>
      <h1>{Math.floor(citySummaryData?.main?.temp)}°C</h1>
    </div>
    <div class="city-summary-data">
      <div class="card">
        <div class="sub-card">
          <div class="sub-card-title">
            <img src={feelslike} alt="feelslike" style="width: 25px" />
            <p>feels like</p>
          </div>
          <p>{Math.floor(citySummaryData?.main.feels_like)}°C</p>
        </div>
        <div class="sub-card">
          <div class="sub-card-title">
            <img src={humidity} alt="humidity" style="width: 20px" />
            <p>humidity</p>
          </div>
          <p>{citySummaryData?.main.humidity}%</p>
        </div>
      </div>
      <div class="card">
        <div class="sub-card">
          <div class="sub-card-title">
            <img src={mintemp} alt="mintemp" style="width: 20px" />
            <p>min temp</p>
          </div>
          <p>{Math.floor(citySummaryData?.main.temp_min)}°C</p>
        </div>
        <div class="sub-card">
          <div class="sub-card-title">
            <img src={maxtemp} alt="maxtemp" style="width: 20px" />
            <p>max temp</p>
          </div>
          <p>{Math.ceil(citySummaryData?.main.temp_max)}°C</p>
        </div>
      </div>
    </div>
  </div>
  <DetailPage {cityDetailData} />
</div>
