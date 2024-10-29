<template>
  <div class="baseBeverage" :style="beverageStyle"></div>
</template>

<script setup lang="ts">
export default{
  data(){
    return{
      baseBeverage: 'black',
      beverageStyle: {}
    };
  },
}

methods: {
  updateAppearance(){
    switch (this.baseBeverage){
      case 'black':
      this.beverageStyle = {
        color: '#2C1608',
      }
      break;
      case 'green':
      this.beverageStyle = {
        color: '#C1E1C1',
      }
      break;
      case 'coffee':
      this.beverageStyle = {
        color: '#5A3825',
      }
      break;
    }
  }
},
mounted() {
  this.updateAppearance();
};
</script>

<style scoped>
.baseBeverage {
  position: relative;
  width: 100%;
  height: 100%;
  bottom: 0;
  animation: pour-tea 2s;
  z-index: 300;
  /* // border-radius: 0.05em 0.05em 2.2em 2.2em; */
}
</style>
