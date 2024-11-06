<template>
  <div class="mug-container">
    <Mug>
      <Cold v-if="isIced" />
      <Hot v-else />
      <Contents>
        <template #top>
          <Creamer 
            v-if="showCreamer" 
            :creamer="creamer" 
            :style="{ zIndex: creamerZIndex }"
          />
        </template>
        <template #mid>
          <Syrup 
            v-if="showSyrup" 
            :syrup="syrup" 
            :style="{ zIndex: syrupZIndex }"
          />
        </template>
        <template #bottom>
          <Base 
            :base="base" 
            :style="{ zIndex: baseZIndex }"
          />
        </template>
      </Contents>
    </Mug>
  </div>
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

// Adjust z-index values
const baseZIndex = computed(() => 1);
const syrupZIndex = computed(() => showSyrup.value ? 2 : 0);
const creamerZIndex = computed(() => showCreamer.value ? 3 : 0);
</script>

<style scoped>
.mug-container {
  position: relative;
  width: 100%;
  height: 100%;
}

.contents {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  overflow: hidden;
}

.base, .syrup, .creamer {
  position: absolute;
  left: 0;
  right: 0;
}

.base {
  bottom: 0;
  height: 100%;
}

.syrup {
  bottom: 0;
  height: 25%; 
}

.creamer {
  top: 0;
  height: 30%; 
}
</style>