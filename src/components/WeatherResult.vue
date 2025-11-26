<script>
export default {
  name: "WeatherResult",
  props: {
    weather: Object,
    error: String,
  },
};
</script>
<template>
  <div>
    <!-- Message d'erreur -->
    <p v-if="error" class="error">{{ error }}</p>

    <!-- Aucune recherche encore -->
    <p v-else-if="!weather" class="info">
      Saisissez une ville pour voir la météo
    </p>

    <!-- Résultat météo -->
    <div
      class="flex flex-col border-green-600 border-2 rounded-2xl my-5 py-3"
      v-else
    >
      <h2>{{ weather.location.name }}, {{ weather.location.country }}</h2>

      <img
        :src="weather.current.condition.icon"
        :alt="weather.current.condition.text"
        class="weather-icon w-[50%] self-center"
      />

      <p class="condition">{{ weather.current.condition.text }}</p>
      <p class="temp">{{ weather.current.temp_c }} °C</p>
      <p>Humidité : {{ weather.current.humidity }} %</p>
      <p>Vent : {{ weather.current.wind_kph }} km/h</p>
    </div>
  </div>
</template>
<style></style>
