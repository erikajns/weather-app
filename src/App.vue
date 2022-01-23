<template>
  <div id="app" :class="weatherCode">
    <main>
      <div class="welcome-message" v-if="showDefault">
        <div class="welcome-message__wrap">
          <h1>WELCOME!</h1>
          <p>Find out the weather</p>
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
  margin: 0;
  padding: 0;
  box-sizing: border-box;
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
  background-color: grey;
}

#app.Thunderstorm {
  background-color: darkblue;
}

#app.Drizzle {
  background-color: lightcyan;
}

#app.Rain {
  background-color: lightgray;
}

#app.Snow {
  background-color: lightsteelblue;
}

#app.Clear {
  background-color: skyblue;
}

main {
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.25),
    rgba(0, 0, 0, 0.75)
  );
}

.welcome-message {
  display: flex;
  justify-content: center;
}

.welcome-message__wrap {
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0 16px 0 16px;
  transition: 0.4s;
  height: 50vh;
  width: 50vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.welcome-message p,
.welcome-message h1  {
  color: white;
}

.welcome-message__button {
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  padding: 10px;
  border-radius: 4px;
  border: none;
  transition: 0.4s;
}
</style>
