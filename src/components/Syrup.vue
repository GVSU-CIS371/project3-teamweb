<template>
  <div class="syrup" :style="syrupStyle" v-if="syrup !== 'none'"></div>
</template>

<script setup lang="ts">
export default{
  data(){
    return{
      syrup : 'hazelnut',
      syrupStyle: {}
    };
  },
}
methods: {
  updateAppearance(){
    switch (this.syrup){
      case 'hazelnut':
      this.syrupStyle = {
        color: 'brown',
      }
      break;
      case 'caramel':
      this.syrupStyle = {
        color: 'lightbrown',
      }
      break;
      case 'vanilla':
      this.syrupStyle = {
        color: 'white',
      }
      break;
    }
  }
},
mounted() {
  this.updateAppearance();
};

</script>
<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  background-color: #c6c6c6;
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
}
</style>
