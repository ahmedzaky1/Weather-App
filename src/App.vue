<template>
  <div class="app">
    <div class="header container h-100 p-5">
      <h1 class="mb-5">Weather App</h1>
      <div class="d-flex justify-content-center h-100">
        <div class="searchbar mx-2 w-50">
          <input
            type="text"
            class="input form-control"
            v-model="city"
            placeholder="Enter a City"
          />
        </div>
        <button class="btn-search btn btn-primary" @click="searchWeather">
          Search <i class="fas fa-search"></i>
        </button>
      </div>
    </div>
    <br />
    <weather-component :city="city" v-if="showWeather"></weather-component>
  </div>
</template>

<script>
import WeatherComponent from "./components/WeatherComponent.vue";

export default (await import("vue")).defineComponent({
  name: "App",
  data() {
    return {
      city: "",
      showWeather: false,
    };
  },
  methods: {
    async searchWeather() {
      this.searchWeather = false;
      await this.$nextTick();
      this.showWeather = true;
    },
  },
  components: { WeatherComponent },
});
</script>

<style>
body {
  background-color: #121212 !important;
}
.header {
  background-color: #212730 !important;
  border-radius: 20px;
  color: #fff;
  text-align: center;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  margin-top: 5rem;
}
.btn-search {
  background-image: linear-gradient(to right, cyan, magenta);
}
.btn-search span {
  margin-right: 7px !important;
}
</style>
