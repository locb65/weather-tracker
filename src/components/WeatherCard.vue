<template>
  <div class="weather-card" v-if="weather">
    <h2>{{ weather.city }}</h2>
    <p><strong class="status-header">Temperature</strong> {{ weather.temperature }}°C or</p>
    <p><strong class="status-header">Condition</strong> {{ weather.condition }}</p>
    <p><strong class="status-header">Humidity</strong> {{ weather.humidity }}%</p>
    <p><strong class="status-header">Wind</strong> {{ weather.wind }}mph</p>
  </div>
</template>

<script setup>
defineProps({
  weather: {
    type: Object,
    required: true,
  },
})
</script>

<style scoped>
.weather-card {
  background: white;
  border-radius: 16px;
  padding: 20px;
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.1);
  max-width: 450px;
}

p {
  margin: 8px;
  padding-right: 8px;
}

h2 {
  margin-bottom: 10px;
}
</style>
