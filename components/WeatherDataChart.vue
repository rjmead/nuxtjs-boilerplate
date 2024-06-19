<template class="min-h-screen">
  <!-- <WeatherLineChart :data="hourlyDataArray" :chartWidth="1000" :chartHeight="400" /> -->
  <WeatherLineChart :data="hourlyData" />
</template>

<script lang="ts" setup>
import { ref, type Ref } from 'vue';
import WeatherLineChart from './WeatherLineChart.vue';
import mockData from '../mockWeatherData.json';

interface HourlyData {
  time: string[];
  temp: number[];
}
const hourlyData: Ref<HourlyData> = ref({
  time: mockData.hourly.time.map((datetimeString) => {
    const date = new Date(datetimeString);
    const options: Intl.DateTimeFormatOptions = { hour: 'numeric', minute: 'numeric', hour12: true };
    return date.toLocaleTimeString('en-US', options);
  }),
  temp: mockData.hourly.temperature_2m
});

// const hourlyDataArray: Ref<HourlyData[]> = ref([]);

// hourlyDataArray.value = mockData.hourly.temperature_2m.map((temperature, index) => {
//   // mockData.hourly.time[index]
//   const datetimeString = mockData.hourly.time[index];
//   const date = new Date(datetimeString);
//   const options: Intl.DateTimeFormatOptions = { hour: 'numeric', minute: 'numeric', hour12: true };
//   const formattedTime = date.toLocaleTimeString('en-US', options);
//   return {
//     time: formattedTime,
//     temp: temperature
//   }
// });

</script>

<style>
#app {
  /* color: #2ecc71 */
}
</style>