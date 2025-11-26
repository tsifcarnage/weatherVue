<script>
import axios from "axios";
import CityInput from "./components/CityInput.vue";
import WeatherResult from "./components/WeatherResult.vue";
const API_KEY = "50ed5a562c6d4d939d1193000252611";
export default {
  components: {
    CityInput,
    WeatherResult,
  },
  data() {
    return {
      weather: null,
      error: "",
    };
  },
  methods: {
    async fetchWeather(city) {
      if (city.trim().length < 3) {
        this.error = "Le nom de la ville doit contenir au moins 3 caractères.";
        this.weather = null;
        return;
      }

      this.error = "";
      try {
        const response = await axios.get(
          `https://api.weatherapi.com/v1/current.json?key=${API_KEY}&q=${city}&aqi=no`
        );
        this.weather = response.data;
      } catch (err) {
        const msg =
          err.response?.data?.error?.message ||
          "Ville introuvable ou erreur réseau.";
        this.error = msg;
        this.weather = null;
      }
    },
  },
};
</script>
<template>
  <h1 class="m-3">Weather Application</h1>
  <CityInput @search="fetchWeather" />
  <WeatherResult :weather="weather" :error="error" />
</template>
<style></style>
