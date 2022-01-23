<template>
  <div class="search-box">
    <input
      type="text"
      class="search-box__bar"
      placeholder="Enter place..."
      v-model="query"
      @keypress="fetchWeatherInfo"
    />
  </div>
</template>

<script>
export default {
  name: "searchBar",
  data() {
    return {
    apiKey: "1c46d1d32df0f228772395763bfcdcc2",
      urlBase: 'https://api.openweathermap.org/data/2.5/',
      query: "",
    };
  },
  methods: {
    fetchWeatherInfo(e) {
      if (e.key == "Enter") {
        fetch(
          `${this.urlBase}weather?q=${this.query}&units=metric&APPID=${this.apiKey}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.setResults);
      }
    },
    setResults(results) {
      this.$emit("keypress", results);
    },
  },
};
</script>

<style lang="css">
.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-box__bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0 16px 0 16px;
  transition: 0.4s;
}

.search-box .search-box__bar:focus {
  box-shadow: 0 0 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0 16px 0;
}
</style>
