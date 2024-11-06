<template>
  <div>
    <Beverage :isIced="currentTemp === 'iced'" :creamer="selectedCreamer" :syrup="selectedSyrup" :base="selectedBase" />
    <div class="mt-4 grid grid-cols-1 gap-4">
      <div>
       
        <div class="flex space-x-4">
          <label v-for="temp in temps" :key="temp" class="flex items-center cursor-pointer">
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
              class="mr-2"
              @change="updateBeverage"
            />
            <span class="capitalize">{{ temp }}</span>
          </label>
        </div>
      </div>
      <div>
        
        <div class="flex space-x-4">
          <label v-for="creamer in creamers" :key="creamer" class="flex items-center cursor-pointer">
            <input
              type="radio"
              name="creamer"
              :id="`c${creamer}`"
              :value="creamer"
              v-model="selectedCreamer"
              class="mr-2"
              @change="updateBeverage"
            />
            <span class="capitalize">{{ creamer }}</span>
          </label>
        </div>
      </div>
      <div>
       
        <div class="flex space-x-4">
          <label v-for="syrup in syrups" :key="syrup" class="flex items-center cursor-pointer">
            <input
              type="radio"
              name="syrup"
              :id="`s${syrup}`"
              :value="syrup"
              v-model="selectedSyrup"
              class="mr-2"
              @change="updateBeverage"
            />
            <span class="capitalize">{{ syrup }}</span>
          </label>
        </div>
      </div>
      <div>
       
        <div class="flex space-x-4">
          <label v-for="base in bases" :key="base" class="flex items-center cursor-pointer">
            <input
              type="radio"
              name="base"
              :id="`b${base}`"
              :value="base"
              v-model="selectedBase"
              class="mr-2"
              @change="updateBeverage"
            />
            <span class="capitalize">{{ base }}</span>
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Beverage from "./components/Beverage.vue";

const temps = ref(["hot", "iced"]);
const creamers = ref([ "No Cream", "Milk", "Cream", "Half-and-Half"]);
const syrups = ref([ "No Syrup", "Vanilla", "Caramel", "Hazelnut"]);
const bases = ref(["Coffee", "Green-tea", "Black-tea"]);

const currentTemp = ref("hot");
const selectedCreamer = ref("No Cream");
const selectedSyrup = ref("No Syrup");
const selectedBase = ref("Coffee");

function updateBeverage() {
  console.log(`Ordered a ${selectedBase.value} with ${selectedCreamer.value} and ${selectedSyrup.value} syrup.`);
}
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