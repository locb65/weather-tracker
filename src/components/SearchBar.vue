<template>
  <div class="search-bar">
    <input v-model="city" type="text" placeholder="Enter a city" @keyup.enter="handleSearch" />

    <button @click="handleSearch">Search</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const city = ref('')

const emit = defineEmits(['search'])

function handleSearch() {
  if (!city.value.trim()) return
  emit('search', city.value.trim())
  city.value = ''
}
</script>

<style scoped>
.search-bar {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 16px;
}

button {
  padding: 12px 18px;
  border: none;
  background: #222;
  color: white;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  background: #444;
}
</style>
