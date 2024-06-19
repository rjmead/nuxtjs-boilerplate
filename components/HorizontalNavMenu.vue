<script setup lang="ts">
const route = useRoute()

const links = [{
  label: 'Home',
  to: `/`
  // to: `${route.path.startsWith('/dev') ? '/dev' : ''}/components/horizontal-navigation`
}, {
  label: 'Today\'s Weather',
  // to: '#'
  to: '/today'
}, {
  label: '3-Day Forecast',
  to: '#'
}]
</script>

<template>
  <UHorizontalNavigation :links="links">
    <template #default="{ link }">
      <span class="group-hover:text-primary relative">{{ link.label }}</span>
    </template>
  </UHorizontalNavigation>
</template>