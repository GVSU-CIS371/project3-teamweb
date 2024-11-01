<template>
  <Mug>
    <Cold v-if="isIced" />
    <Hot v-else />
    <Contents>
      <template v-slot:top>
        <Creamer v-if="showCreamer" :creamer="creamer" :style="{ zIndex: creamerZIndex }" />
      </template>
      <template v-slot:mid>
        <Syrup v-if="showSyrup" :syrup="syrup" :style="{ zIndex: syrupZIndex }" />
      </template>
      <template v-slot:bottom>
        <Base :base="base" :style="{ zIndex: baseZIndex }" />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

interface Props {
  isIced: boolean;
  creamer: string;
  syrup: string;
  base: string;
}

const props = defineProps<Props>();

const showCreamer = computed(() => props.creamer !== 'No Cream');
const showSyrup = computed(() => props.syrup !== 'No Syrup');

// Define the dynamic z-index for each layer
const creamerZIndex = computed(() => (showCreamer.value && !showSyrup.value ? 5 : 3));
const syrupZIndex = computed(() => (showSyrup.value ? 3 : 0));
const baseZIndex = computed(() => 2);
</script>

<style scoped>
.contents {
  position: relative;
  height: 100%;
  width: 100%;
}

.base, .syrup, .creamer {
  position: absolute;
  left: 0;
  right: 0;
}
.base {
  bottom: 0;
}
.syrup {
  bottom: 0;
}
.creamer {
  top: 0;
}
</style>
