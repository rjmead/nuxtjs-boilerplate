<template>
  <div>
    <!-- <Line class="min-h-50" :data="chartData" :options="chartOptions" /> -->
    <Line :style="myStyles" :data="chartData" :options="chartOptions" />
  </div>
</template>
<script lang="ts" setup>
  import { Line } from 'vue-chartjs';
  import {
    Chart as ChartJS,
    Title,
    Tooltip,
    Legend,
    BarElement,
    PointElement, // make sure this is imported
    LineElement,
    CategoryScale,
    LinearScale,
  } from 'chart.js';
  import { ref } from 'vue';
  ChartJS.register(
    Title,
    Tooltip,
    Legend,
    BarElement,
    PointElement, // make sure this is imported
    LineElement,
    CategoryScale,
    LinearScale
  );

  // set props
  const props = defineProps({
    data: {
      type: Object,
      required: true,
    },
  });

  // Set chart data
  // Props are passed from parent component WeatherDataChart.vue
  // label: Temperature
  // labels array of time
  // data array of temperature
  const chartData = ref({
    labels: props.data.time, // This would be the time of day
    // labels: ['January', 'February', 'March', 'April', 'May'], // This would be the time of day
    datasets: [
      {
        label: 'Temperature',
        backgroundColor: 'rgb(163, 230, 53)',
        data: props.data.temp.filter((temp: any) => temp > 70),
      },
      {
        label: 'Temperature',
        backgroundColor: 'rgb(163, 230, 53)',
        data: props.data.temp.filter((temp: any) => temp <= 70), // for showing different color nodes. I will need to find out how to keep them linear/congruent in time order
      },
    ],
  });

  const chartOptions = ref({
    responsive: true,
    maintainAspectRatio: false,
  });

  
    const myStyles = {
        height: `${400}px`,
        // position: 'relative'
      }
    
</script>

<style>
/* style the dataset with the temperature label */


</style>
