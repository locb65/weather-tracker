<template>
  <div class="weather-card">
    <h2>Tokyo</h2>
    <p><strong class="status-header">Temperature</strong>1°C</p>
    <p><strong class="status-header">Condition</strong>Cloud but Windy</p>
    <p><strong class="status-header">Humidity</strong>82%</p>
    <p><strong class="status-header">Wind</strong>25mph</p>
  </div>
</template>

<style scoped>
.weather-card {
  background: white;
  border-radius: 16px;
  padding: 20px;
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.1);
  max-width: 450px;
}

.status-header {
  margin: 8px 0;
}

h2 {
  margin-bottom: 10px;
}
</style>
