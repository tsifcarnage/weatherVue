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
    <p v-if="error" class="py-3">Aucune correspondance trouvée</p>

    <!-- Aucune recherche encore -->
    <p v-else-if="!weather" class="py-3">
      Saisissez une ville pour voir la météo
    </p>

    <!-- Résultat météo -->
    <div
      class="shadowing flex flex-col gap-4 border-green-600 border-2 rounded-2xl my-5 py-10"
      v-else
    >
      <h2 class="font-bold text-3xl text-green-500">
        {{ weather.location.name }}, {{ weather.location.country }}
      </h2>

      <img
        :src="weather.current.condition.icon"
        :alt="weather.current.condition.text"
        class="weather-icon w-[30%] self-center"
      />

      <p class="condition">{{ weather.current.condition.text }}</p>
      <p class="text-3xl font-bold">{{ weather.current.temp_c }} °C</p>
      <p>Humidité : {{ weather.current.humidity }} %</p>
      <p>Vent : {{ weather.current.wind_kph }} km/h</p>
    </div>
  </div>
</template>
<style scoped>
.shadowing {
  box-shadow: 0px 0px 7px 5px green;
}
</style>
