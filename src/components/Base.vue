<template>
  <div class="baseBeverage" :style="baseStyle"></div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  base: string;
}>();

const baseStyle = computed(() => {
  const colors = {
    'Coffee': '#3c2f2f',
    'Green-tea': '#d0e5a0',
    'Black-tea': '#8b4513'
  };
  return {
    backgroundColor: colors[props.base] || '#3c2f2f'
  };
});
</script>

<style scoped>
.baseBeverage {
  position: relative;
  width: 100%;
  height: 100%;
  bottom: 0;
  animation: pour-tea 2s;
  z-index: 300;
}

@keyframes pour-tea {
  0% { height: 0; }
  100% { height: 100%; }
}
</style>