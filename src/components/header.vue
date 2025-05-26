<script setup>
import { ref } from 'vue'
import { Icon } from '@iconify/vue'

const title = ref("SVGoo");
const isClicked = ref(false); // Start with false to be hidden

function toggleSidebar() {
  isClicked.value = !isClicked.value;
}
</script>

<template>
  <div class="top">
     <Icon icon="material-symbols:menu-rounded" width="40" height="40" @click="toggleSidebar" />
    <h1>{{ title }}</h1>
   
  </div>
  <Transition name="slide">
  <div v-if="isClicked" class="sideBar">
    <h1>Hii</h1>
    <Icon icon="meterial-symbols:cross" width="40" height="40" @click="toggleSidebar" class="cross" />
    
  </div>
  </Transition>
  <Transition name="shadow">
    <div class="shadow"></div>
  </Transition>
</template>

<style scoped>
.top {
  position: fixed;
  top: 0;
  width: 100vw;
  height: 70px;
  background: #0077b6;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  z-index: 100; /* Ensure it's above other elements */
}

.sideBar {
  position: fixed;
  top: 0; /* Below the top bar */
  left: 0;
  width: 200px;
  height: calc(100vh - 70px); /* Full height minus top bar */
  background: #00b4d8;
  z-index: 101;
  transform: translateX(0px);
  
  .cross{
  border: 2px solid #000;
  }
}

.shadow{
 background: #000000aa;
 height:100vh;
 width:100vw;
 position:absolute;
 
 }
 
 .slide-enter-active, .slide-leave-active{
  transition: all 0.5s ease;
 }
 
.shadow-enter-active,
.shadow-leave-active {
  transition: transform 0.5s ease;
}


.slide-enter-from{
  transform: translateX(-200px);
}
.slide-leave-to{
transform: translateX(-200px);
}

.shadow-enter-from , .shadow-leave-to{
opacity:0;
margin-left: 200px;
}

</style>