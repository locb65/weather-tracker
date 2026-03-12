<script setup>
import { ref } from 'vue'
import SearchBar from './components/SearchBar.vue'
import WeatherCard from './components/WeatherCard.vue'

const weather = ref({
  city: 'Tokyo',
  temperature: 77,
  humidity: 85,
  condition: 'Cloudy, windy',
  wind: 15,
})
const message = ref('')
function searchWeather(city) {
  message.value = `You searched for ${city}`

  weather.value = {
    city,
    temperature: 22,
    condition: 'Sunny',
    humidity: 55,
    wind: 10,
  }
}
</script>

<template>
  <div>
    <SearchBar @search="searchWeather" />
    <WeatherCard v-if="weather" :weather="weather" />
  </div>
</template>

<style scoped></style>
