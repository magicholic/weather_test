<script setup>
import { ref } from 'vue'

const city = ref('')
const emit = defineEmits(['updateCity'])

const updateCity = () => {
  emit('updateCity', city.value)
}
</script>

<template>
  <div>
    <input type="text" placeholder="Enter city..." v-model="city" />
    <button @click="updateCity">Get Weather</button>
  </div>
</template>
