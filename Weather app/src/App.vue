<script setup>
import { ref } from "vue";

const baseUrl = ref('api.weatherapi.com/')
const key = ref('8190f950589d4af1a48215330222607')

const location = ref("");
let data = ref({})

function getWeather(e) {
  console.log(location.value)
  if (e.key == 'Enter') {
    fetch(`http://${baseUrl.value}v1/current.json?key=${key.value} &q=${location.value}$api=yes`, {
      headers: {
        "Access-Control-Allow-Origin": baseUrl.value,
      },
    })
      .then((res) => {
        return res.json()
      })
      .then((dataToVar))
  }
}

function dataToVar(results) {
  console.log(results)
  data = results
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
    {{ data.location }}
    <div class="info">
      <h1 id="location">Moscow, Russia</h1>
      <h2 id="current time">0:58 -- July 28</h2>

      <div class="temp-box">
        <h1>+ 22</h1>
      </div>
    </div>
  </body>
</template>
