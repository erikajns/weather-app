<template>
  <div id="app">
    <main>
      <search-bar @keypress="onSearch"></search-bar>
      <weather-results :weatherInfo="weather"></weather-results>
    </main>
  </div>
</template>

<script>
import SearchBar from './components/Search-Bar/Search-Bar.vue';
import WeatherResults from './components/Weather-Results/Weather-Results.vue';

export default {
  components: { SearchBar, WeatherResults },
  name: "App",
  data() {
    return {
      weather: {},
    };
  },
  methods: {
    onSearch(results){
      console.log(results);
      this.weather = results;
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
  font-family: "montserrat", sans-serif;
}

#app {
  background-image: url("./assets/cold-bg.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app.warm {
  background-image: url('./assets/warm-bg.jpg');
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
</style>
