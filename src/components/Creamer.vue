<template>
  <div class="froth" :style="frothStyle">
    <div v-for="i in 5" :key="i" class="foam" :style="foamStyle"></div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  creamer: string;
}>();

const frothStyle = computed(() => {
  const colors = {
    'No Cream': 'transparent',
    'Milk': '#f0e6d2',
    'Cream': '#fff5e6',
    'Half-and-Half': '#fff0db'
  };
  return {
    backgroundColor: colors[props.creamer] || 'transparent'
  };
});

const foamStyle = computed(() => {
  return {
    backgroundColor: props.creamer === 'No Cream' ? 'transparent' : '#ffffff'
  };
});
</script>

<style lang="scss" scoped>
.froth {
  overflow: visible;
  transform: translateY(400%);
  position: relative;
  height: 20%;
  width: 100%;
  animation: pour-tea 2s 2s forwards;
}

.foam {
  display: block;
  border-radius: 30px;
  height: 40px;
  width: 40px;
  position: absolute;
}

.foam:nth-child(1) { top: 0px; left: -3px; }
.foam:nth-child(2) { top: 0px; left: 55px; }
.foam:nth-child(3) { width: 30px; height: 30px; border-radius: 40px; top: 3px; left: 30px; }
.foam:nth-child(4) { width: 30px; height: 30px; border-radius: 45px; top: 5px; right: -2px; }
.foam:nth-child(5) { top: 2px; right: 10px; }

@keyframes pour-tea {
  0% { transform: translateY(400%); }
  100% { transform: translateY(0); }
}
</style>