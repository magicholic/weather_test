<script setup>
import { ref, watch } from 'vue'
import { API_KEY } from '@/data/credentials'

const props = defineProps({ city: String })
const results = ref({})

async function fetchWeatherData() {
  try {
    const response = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?q=${props.city}&appid=${API_KEY}&units=metric`,
    )
    results.value = await response.json()
  } catch (error) {
    console.error('Error fetching weather data:', error)
  }
}
watch(
  () => props.city,
  (newCity) => {
    if (newCity) {
      fetchWeatherData()
    }
  },
)
</script>

<template>
  <div v-if="props.city">
    <h1>Weather Result</h1>
    <h3>City - {{ props.city }}</h3>
    <div v-if="results.main">
      <p>Temperature: {{ results.main.temp }} °C</p>
      <p>Humidity: {{ results.main.humidity }} %</p>
      <p>Weather: {{ results.weather[0].description }}</p>
    </div>
  </div>
</template>
