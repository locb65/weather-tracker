<script setup>
import { ref } from 'vue'
import SearchBar from './components/SearchBar.vue'
import WeatherCard from './components/WeatherCard.vue'

const weather = ref(null)
const message = ref('')
const loading = ref(false)

async function searchWeather(city) {
  const apiKey = import.meta.env.VITE_WEATHER_API_KEY
  if (!apiKey) {
    message.value = 'Missing API key. Please add an API key to your .env file'
    return
  }

  loading.value = true
  message.value = ''
  weather.value = null

  try {
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${encodeURIComponent(city)}&appid=${apiKey}&units=metric`
    const response = await fetch(url)
    const data = await response.json()
    console.log(data)

    if (!response.ok) {
      throw new Error(data.message || 'Failed to fetch weather')
    }

    weather.value = {
      city: data.name,
      temperature: data.main.temp,
      condition: data.weather[0].main,
      humidity: data.main.humidity,
      wind: data.wind.speed,
    }
  } catch (error) {
    message.value = error.message || 'Something went wrong.'
  } finally {
    loading.value = false
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
