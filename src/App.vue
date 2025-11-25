<script setup>
import { ref } from 'vue'
import InputComp from './components/InputComp.vue'
import WeatherCheck from './components/WeatherCheck.vue'

const enteredCity = ref('')
function handleUpdateCity(data) {
  enteredCity.value = data
}
</script>

<template>
  <div>
    <div id="inputField">
      <InputComp @update-city="handleUpdateCity" />
    </div>
    <WeatherCheck :city="enteredCity" />
  </div>
</template>

<style scoped></style>
