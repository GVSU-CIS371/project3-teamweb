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
          />
        </template>
        <template #mid>
          <Syrup 
            v-if="showSyrup" 
            :syrup="syrup"
          />
        </template>
        <template #bottom>
          <Base 
            :base="base"
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
</script>