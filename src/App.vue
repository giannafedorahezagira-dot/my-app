<script setup>
import { ref } from 'vue'

/* DATA */
const search = ref('')

const city = ref('Warren')
const state = ref('Michigan')

const temperature = ref(70)
const high = ref(74)
const low = ref(68)

const weatherType = ref('Sunny ☀️')

/* FUNCTION (THIS MAKES IT WORK) */
const searchWeather = () => {

  const value = search.value.toLowerCase().trim()

  if (value === 'kigali') {

    city.value = 'Kigali'
    state.value = 'Rwanda'
    temperature.value = 25
    high.value = 28
    low.value = 20
    weatherType.value = 'Sunny ☀️'

  }

  else if (value === 'paris') {

    city.value = 'Paris'
    state.value = 'France'
    temperature.value = 18
    high.value = 22
    low.value = 14
    weatherType.value = 'Cloudy ☁️'

  }

  else if (value === 'london') {

    city.value = 'London'
    state.value = 'England'
    temperature.value = 12
    high.value = 15
    low.value = 8
    weatherType.value = 'Rainy 🌧️'

  }

  else {

    city.value = 'Unknown'
    state.value = 'No Data'
    temperature.value = 0
    high.value = 0
    low.value = 0
    weatherType.value = 'Not Found ❌'

  }
}
</script>

<template>

<div id="app">

  <div class="app">

    <!-- TITLE -->
    <div class="header">
      <h1>⚙ The Local Weather</h1>
      <p>Vue Weather App</p>
    </div>

    <!-- SEARCH -->
    <div class="search-box">

      <input
        type="text"
        v-model="search"
        placeholder="Search city..."
        @keyup.enter="searchWeather"
      />

      <button @click="searchWeather">
        Search Weather
      </button>

    </div>

    <!-- WEATHER CARD -->
    <div class="weather-card">

      <div class="left">

        <h2>{{ city }}</h2>
        <p>{{ state }}</p>
        <span class="type">{{ weatherType }}</span>

      </div>

      <div class="right">

        <h1>{{ temperature }}°</h1>

        <small>
          H: {{ high }}° L: {{ low }}°
        </small>

      </div>

    </div>

  </div>

</div>

</template>

<style>

/* RESET */
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

/* FULL SCREEN CENTER */
html, body, #app{
  width:100%;
  height:100%;
  display:flex;
  justify-content:center;
  align-items:center;
  background:#111;
  font-family: Arial;
}

/* APP BOX */
.app{
  width:420px;
  background:#0a6c8f;
  padding:30px;
  border-radius:12px;
  color:white;
}

/* HEADER */
.header{
  text-align:center;
  margin-bottom:30px;
}

/* SEARCH */
.search-box{
  margin-bottom:20px;
}

.search-box input{
  width:100%;
  padding:12px;
  border:none;
  border-bottom:2px solid white;
  background:transparent;
  color:white;
  outline:none;
  margin-bottom:10px;
}

.search-box button{
  width:100%;
  padding:12px;
  border:none;
  background:#084f69;
  color:white;
  cursor:pointer;
}

/* WEATHER CARD */
.weather-card{
  background:#084f69;
  padding:20px;
  border-radius:10px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}

.left h2{
  font-size:30px;
}

.right{
  text-align:right;
}

.right h1{
  font-size:50px;
}

.type{
  display:inline-block;
  margin-top:8px;
  font-size:14px;
  background:rgba(255,255,255,0.2);
  padding:5px 10px;
  border-radius:20px;
}

</style>