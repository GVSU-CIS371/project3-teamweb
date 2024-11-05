<template>
  <div>
    <Beverage :isIced="currentTemp === 'Cold'" />
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
    </ul>
  </div>
  <div>
    <Beverage :base="currentBase === 'Coffee'" />
    <ul>
      <li>
        <template v-for="base in base" :key="base">
          <label>
            <input
              type="radio"
              name="Coffee"
              :id="`r${base}`"
              :value="base"
              v-model="currentBase"
            />
            {{ temp }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="base in base" :key="base">
          <label>
            <input
              type="radio"
              name="Black Tea"
              :id="`r${base}`"
              :value="base"
              v-model="currentBase"
            />
            {{ temp }}
          </label>
        </template>
      </li> 
      <li>
        <template v-for="base in base" :key="base">
          <label>
            <input
              type="radio"
              name="Green Tea"
              :id="`r${base}`"
              :value="base"
              v-model="currentBase"
            />
            {{ temp }}
          </label>
        </template>
      </li>     
    </ul>
  </div>
  <div>
    <Beverage :showCreamer="currentCreamer !=== 'No Creamer'" />
    <ul>
      <li>
        <template v-for="creamer in creamer" :key="creamer">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`r${creamer}`"
              :value="Milk"
              v-model="currentCreamer"
            />
            {{ creamer }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="creamer in creamer" :key="creamer">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`r${creamer}`"
              :value="Cream"
              v-model="currentCreamer"
            />
            {{ creamer }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="creamer in creamer" :key="creamer">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`r${creamer}`"
              :value="Half-and-Half"
              v-model="currentCreamer"
            />
            {{ creamer }}
          </label>
        </template>
      </li>
    </ul>
  </div>

    <div>
    <Beverage :showSyrup="currentSyrup !=== 'No Syrup'" />
    <ul>
      <li>
        <template v-for="syrup in syrup" :key="syrup">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`r${syrup}`"
              :value="Vanilla"
              v-model="currentSyrup"
            />
            {{ syrup }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="syrup in syrup" :key="syrup">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`r${syrup}`"
              :value="Caramel"
              v-model="currentSyrup"
            />
            {{ syrup }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="syrup in syrup" :key="syrup">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`r${syrup}`"
              :value="Hazelnut"
              v-model="currentSyrup"
            />
            {{ syrup }}
          </label>
        </template>
      </li>
    </ul>
  </div>

</template>

<script setup lang="ts">
import { ref } from "vue";
import Beverage from "./components/Beverage.vue";
// Define reactive data
const temps = ref(["Hot", "Cold"]);
const currentTemp = ref("Hot");
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
