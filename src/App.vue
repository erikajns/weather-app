<template>
  <div id="app" :class="weatherCode">
    <main>
      <div class="welcome-message" v-if="showDefault">
        <div class="welcome-message__wrap">
          <h1>WELCOME!</h1>
          <p>Find out the weather from all countries around the world.</p>
          <p>
            Instructions: Just type in the country you want to know the weather
            in the search box!
          </p>
          <button class="welcome-message__button" @click="onHide">
            Find weather
          </button>
        </div>
      </div>
      <search-bar @keypress="onSearch" :showBar="showSearchBar"></search-bar>
      <weather-results :weatherInfo="weather"></weather-results>
    </main>
  </div>
</template>

<script>
import SearchBar from "./components/Search-Bar/Search-Bar.vue";
import WeatherResults from "./components/Weather-Results/Weather-Results.vue";

export default {
  components: { SearchBar, WeatherResults },
  name: "App",
  data() {
    return {
      weather: {},
      weatherCode: {},
      showSearchBar: false,
      showDefault: true,
    };
  },
  methods: {
    onSearch(results) {
      console.log(results);
      this.weather = results;
      this.weatherCode = this.weather.weather[0].main;
    },
    onHide(event) {
      this.showSearchBar = true;
      this.showDefault = false;
      console.log(event + "clicked");
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "muli", sans-serif;
}

#app {
  background-image: url("./assets/city-sunset-bg.jpeg");
  background-size: cover;
  transition: 0.4s;
}

#app.Clouds {
  background-image: url("./assets/clouds-bg.jpeg");
  transition: 0.4s;
}

#app.Thunderstorm {
  background-image: url("./assets/thunder-bg.jpeg");
  transition: 0.4s;
}

#app.Drizzle {
  background-image: url("./assets/drizzle-bg.jpeg");
  transition: 0.4s;
}

#app.Rain {
  background-image: url("./assets/rain-bg.jpeg");
  transition: 0.4s;
}

#app.Snow {
  background-image: url("./assets/snow-bg.jpeg");
  transition: 0.4s;
}

#app.Clear {
  background-image: url("./assets/clear-bg.jpeg");
  transition: 0.4s;
}
#app.Fog {
  background-image: url("./assets/fog-bg.jpeg");
  transition: 0.4s;
}
#app.Tornado {
  background-image: url("./assets/tornado-bg.jpeg");
  transition: 0.4s;
}

main {
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.25),
    rgba(0, 0, 0, 0.75)
  );
  min-height: 100vh;
  padding: 25px;
}

.welcome-message {
  display: flex;
  justify-content: center;
  padding-top: 10%;
}

.welcome-message__wrap {
  align-items: center;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0 16px 0 16px;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 50vh;
  min-width: 50vh;
  padding: 5%;
  text-align: center;
  transition: 0.4s;
}

.welcome-message p,
.welcome-message h1 {
  color: white;
  padding-bottom: 10px;
}

.welcome-message__button {
  background-color: cadetblue;
  border: none;
  border-radius: 4px;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
  color: white;
  font-size: 20px;
  margin-top: 25px;
  padding: 10px;
  transition: 0.4s;
}
</style>
