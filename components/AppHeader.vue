<template #header>
  <UCard class="mt-10">
    <div class="flex justify-between items-center">
      <h1 class="font-mono text-xl">
        <slot />
      </h1>
      <ColorScheme>
        <USelect v-model="$colorMode.preference" :options="['system', 'light', 'dark']" />
      </ColorScheme>
    </div>
    <HorizontalNavMenu />
  </UCard>
</template>


<script lang="ts" setup>

</script>

<style></style>