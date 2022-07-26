<script setup>
import { ref } from "vue";

const baseUrl = ref('api.weatherapi.com/')
const key = ref('8190f950589d4af1a48215330222607')

const location = ref("");
const data = ref({})

function getWeather(enter) {
  if (enter.key == "Enter") {

  }
}

async function fetchInfo() {
  const adress = `http://${baseUrl}/v1/current.json?key=${key}&q=${location}$api=yes`
}
</script>

<template>
  <h1>Weather app</h1>
  <body>
    <input
      type="text"
      id="search-bar"
      placeholder="Moscow"
      v-model="location"
      @keypress="getWeather"
    />
    // eslint-disable-next-line prettier/prettier
    {{ location }}
    <div class="info">
      <h1 id="location">Moscow, Russia</h1>
      <h2 id="current time">0:58 -- July 28</h2>

      <div class="temp-box">
        <h1>+ 22</h1>
      </div>
    </div>
  </body>
</template>
