<script>
  import clock from '../assets/clock.png';

  export let weather;

</script>

<div class="today-main">
  <div class="today-card">
    <div class="sub-card-title">
      <img src={clock} alt="clock" style="width: 20px" />
      {weather?.dt_txt?.slice(11, 16)}
    </div>
    <div class="today-card-header">
      <img
        src={`https://openweathermap.org/img/wn/${weather?.weather[0].icon}.png`}
        alt={weather.weather[0].description}
      />
    </div>
    <div class="today-card-body">
      <div class="card-title">
        {Math.floor(weather?.main.temp)}°C
      </div>
    </div>
  </div>
</div>