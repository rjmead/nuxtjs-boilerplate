<template>
    <UContainer class="m-10">
        <ul class="list-disc">
            <li v-for="paragraph in paragraphs" :key="paragraph.id">{{ paragraph.text }}</li>
        </ul>
    
        <UButton class="m-5" icon="i-heroicons-book-open" to="https://open-meteo.com/en/docs" target="_blank">
            Open-Meteo Weather Forecast API
        </UButton>
    </UContainer>
</template>

<script lang="ts" setup>

const paragraphs = [
    { id: 1, text: '#1  Click button to find my current location, or search for a major city on map.' },
    { id: 2, text: '#2  Show map of current radar preview for location' },
    { id: 3, text: '#3  Dashboard Key Datapoints such as Temp. Precip. Wind. UV Index.' },
    { id: 4, text: '#4  Chart data over time on a multidimensional chart with highlights' }
]
</script>