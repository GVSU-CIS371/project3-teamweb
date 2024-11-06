<template>
  <div class="syrup" :style="syrupStyle"></div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  syrup: string;
}>();

const syrupStyle = computed(() => {
  const colors = {
    'No Syrup': 'transparent',
    'Vanilla': '#f3e5ab',
    'Caramel': '#d2691e',
    'Hazelnut': '#c68a4c'
  };
  return {
    backgroundColor: colors[props.syrup] || 'transparent'
  };
});
</script>

<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
}

// @keyframes pour-tea {
//   0% { transform: translateY(400%); }
//   100% { transform: translateY(0); }
// }
</style>