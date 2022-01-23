<template>
  <div class="results" v-if="weatherInfo.main">
    <div class="results__location-box">
      <div class="results__location-box__location">
        {{ weatherInfo.name }}, {{ weatherInfo.sys.country }}
      </div>
    </div>

    <div class="results__weather-box">
      <div class="results__weather-box__temperature">{{ Math.round(weatherInfo.main.temp) }}°</div>
      <div class="results__weather-box__weather">Rain</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "weatherResults",
  props: {
    weatherInfo: {
      type: Object,
      default() {
        return {};
      },
    },
  },
};
</script>

<style lang="css">
.results__location-box .results__location-box__location {
  color: white;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.results__weather-box {
  text-align: center;
}

.results__weather-box .results__weather-box__temperature {
  display: inline-block;
  padding: 10px 25px;
  color: white;
  font-size: 102px;
  font-weight: 900;

  text-shadow: rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0;

  box-shadow: 3px 6px rgba(255, 255, 255, 0.25);
}

.results__weather-box .results__weather-box__weather {
  color: white;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
</style>
