<template>
<div class="container">
  <NavComp/>
<router-view></router-view>
</div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import NavComp from './components/NavComp.vue';



export default {
  name: 'App',
  components: {
   //HelloWorld
   NavComp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


.container{
  background-color: coral;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
}
</style>
