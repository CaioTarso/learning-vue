<template>
  <div v-if="weather && weather.weather && weather.weather[0]" class="weather">
    <img :src="iconUrl" :alt="weather.weather[0].description" width="30" />
    <span>{{ weather.name }}: {{ Math.round(weather.main.temp) }}°C</span>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const weather = ref(null)
const iconUrl = ref('')
const API_KEY = process.env.VUE_APP_API_KEY
console.log('API response:', API_KEY)

onMounted(() => {
  navigator.geolocation.getCurrentPosition(async (position) => {
    const { latitude, longitude } = position.coords
    const url = `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&appid=${API_KEY}&units=metric&lang=pt_br`

    try {
      const res = await fetch(url)
      const data = await res.json()
      console.log('API reponse:', data)
      if (!data.weather) {
        console.error('Erro na resposta da apu:', data)
        return
      }
      weather.value = data
      iconUrl.value = `https://openweathermap.org/img/wn/${data.weather[0].icon}.png`
    } catch (error) {
      console.error('Erro ao buscar o clima:', error)
    }
  })
})
</script>

<style>
 .weather {
  border-style:solid;
  border-width: 2px;
  border-color: #fff; /* branco */
  padding: 8px;
  border-radius: 8px; /* opcional, deixa os cantos arredondados */
  display: inline-flex;
  align-items: center;
  gap: 8px;
}
</style>