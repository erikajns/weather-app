<template>
  <div class="search-box" v-if="showBar">
    <input
      type="text"
      class="search-box__bar"
      placeholder="Enter country..."
      v-model="query"
      @keypress="fetchWeatherInfo"
    />
  </div>
</template>

<script>
export default {
  name: "searchBar",
  props: {
    showBar: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      apiKey: "1c46d1d32df0f228772395763bfcdcc2",
      urlBase: "https://api.openweathermap.org/data/2.5/",
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
  margin-bottom: 30px;
  width: 100%;
}

.search-box .search-box__bar {
  appearance: none;
  background: none;
  background-color: rgba(255, 255, 255, 0.5);
  border: none;
  border-radius: 0 16px 0 16px;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
  color: #313131;
  display: block;
  font-size: 20px;
  outline: none;
  padding: 15px;
  transition: 0.4s;
  width: 100%;
}

.search-box .search-box__bar:focus {
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0 16px 0;
  box-shadow: 0 0 16px rgba(0, 0, 0, 0.25);
}
</style>
