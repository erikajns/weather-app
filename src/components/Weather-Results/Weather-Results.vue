<template>
  <div class="results" v-if="weatherInfo.main">
    <div class="results__location-box">
      <div class="results__location-box__location">
        {{ weatherInfo.name }}, {{ weatherInfo.sys.country }}
        <font-awesome-icon icon="map-pin" />
      </div>
    </div>

    <div class="results__weather-box">
      <div class="results__weather-box__temperature">
        {{ Math.round(weatherInfo.main.temp) }}°C

        <p class="results__weather-box__max-min-temperature">
          Max. <b>{{ Math.round(weatherInfo.main.temp_max) }}°C</b>  /  Min.
          {{ Math.round(weatherInfo.main.temp_min) }}°C
        </p>
      </div>
      <p class="results__weather-box__feels-like-temperature">
        Feels Like: {{ Math.round(weatherInfo.main.feels_like) }}°C
      </p>
      <div class="results__weather-box__weather">
        {{ weatherInfo.weather[0].main }}
      </div>
      <div class="results__weather-box__weather-description">
        <img
          :src="this.urlBaseOne + weatherInfo.weather[0].icon + this.urlBaseTwo"
        />
        <p>
          {{ weatherInfo.weather[0].description }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faMapPin } from "@fortawesome/free-solid-svg-icons";

library.add(faMapPin);

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
  data() {
    return {
      urlBase: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weatherType: "",
      urlBaseOne: "http://openweathermap.org/img/wn/",
      urlBaseTwo: "@2x.png",
    };
  },
  methods: {
    setWeatherBg() {
      this.weatherType = this.weatherInfo.weather[0].main;
    },
  },
};
</script>

<style lang="css">
.results__location-box .results__location-box__location,
.results__weather-box__feels-like-temperature {
  color: white;
  font-size: 20px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.results__weather-box {
  text-align: center;
}

.results__weather-box .results__weather-box__temperature {
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  box-shadow: 3px 6px rgba(255, 255, 255, 0.25);
  color: white;
  display: inline-block;
  font-size: 102px;
  font-weight: 900;
  margin: 30px 0;
  padding: 10px 25px;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.results__weather-box .results__weather-box__max-min-temperature {
  color: white;
  font-size: 20px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.results__weather-box .results__weather-box__weather {
  color: white;
  font-size: 48px;
  font-style: italic;
  font-weight: 700;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.results__weather-box__weather-description {
  align-items: center;
  color: white;
  display: flex;
  font-size: 15px;
  font-weight: 300;
  height: auto;
  justify-content: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.results__weather-box__weather-description img {
  width: 30px;
}
</style>
