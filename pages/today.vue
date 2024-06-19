<!-- Purpose of this page is to display the 1 day forecast for today based on preset variables -->
<template>
  <div>
    <button class="btn btn-blue" @click="fetchData" v-if="false">
      Fetch Weather Data
    </button>
    <h1 class="mt-10 text-4xl text-center underline">Today's Weather</h1>
    
    <ClientOnly>
      <p>{{ todayDate }}</p>
      <p>{{ todayTime }}</p>
    </ClientOnly>

    <!-- <WeatherDataTable :weatherData="weatherData" /> -->

    <div class="m-10">
      <h1>Temperature</h1>
      <WeatherDataChart />
    </div>
  </div>
</template>

<script lang="ts" setup>
// https://api.open-meteo.com/v1/forecast?latitude=42.3314&longitude=-83.0457&hourly=temperature_2m,relative_humidity_2m,precipitation_probability,weather_code,wind_speed_10m,wind_direction_10m,wind_gusts_10m,uv_index&temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch&timezone=America%2FNew_York&forecast_days=1

import { ref } from 'vue'
import mockdata from '../mockWeatherData.json'
import WeatherDataChart from '~/components/WeatherDataChart.vue';


// state
const weatherData = ref({})


// Set state variables
const today = new Date();
const todayDate = today.toDateString();
const todayTime = today.toTimeString();

// Set API variables
const latitude = 42.3314;
const longitude = -83.0457;

// Set API URL
const apiURL = `https://api.open-meteo.com/v1/forecast?latitude=${latitude}&longitude=${longitude}&hourly=temperature_2m,relative_humidity_2m,precipitation_probability,weather_code,wind_speed_10m,wind_direction_10m,wind_gusts_10m,uv_index&temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch&timezone=America%2FNew_York&forecast_days=1`;

// Fetch API data
async function fetchData() {
    // Use mockData from mockWeatherData.json in root
    const data = await mockdata;
    // const data = await response.json();
    console.log(data);
    weatherData.value = data;

    // const response = await fetch(apiURL);
    // const data = await response.json();
    // console.log(data);
    // weatherData.value = data;
  }

  // onMounted(() => {
    
  //  });
</script>

<style>
  .btn {
    @apply font-bold py-2 px-4 rounded;
  }
  .btn-blue {
    @apply bg-blue-500 text-white;
  }
  .btn-blue:hover {
    @apply bg-blue-700;
  }
</style>
