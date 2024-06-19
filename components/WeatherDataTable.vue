<template>
  <div>
    <table v-if="weatherData?.hourly">
      <thead>
        <tr>
          <th v-for="(unit, key) in weatherData.hourly_units" :key="key">
            {{ String(key).replace('_', ' ') }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(time, index) in weatherData.hourly.time" :key="index">
          <td>{{ time }}</td>
          <td>{{ weatherData.hourly.temperature_2m[index] }}</td>
          <td>{{ weatherData.hourly.relative_humidity_2m[index] }}</td>
          <td>{{ weatherData.hourly.precipitation_probability[index] }}</td>
          <td>{{ weatherData.hourly.weather_code[index] }}</td>
          <td>{{ weatherData.hourly.wind_speed_10m[index] }}</td>
          <td>{{ weatherData.hourly.wind_direction_10m[index] }}</td>
          <td>{{ weatherData.hourly.wind_gusts_10m[index] }}</td>
          <td>{{ weatherData.hourly.uv_index[index] }}</td>
        </tr>
      </tbody>
    </table>
    <p v-else>Loading...</p>
  </div>
</template>

<script lang="ts" setup>
import { defineProps } from 'vue';

// Define the 'weatherData' property in the component's type definition
const props = defineProps({
  weatherData: {
    type: Object,
    required: true,
  },
});
</script>

<style>

</style>

<script lang="ts" setup>

</script>

<style>

</style>