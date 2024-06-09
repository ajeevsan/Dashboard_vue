<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <DashboardComponent/> -->
    <!-- <TestComponent/> -->
     <LgDashboard/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import DashboardComponent from './components/DashboardComponent.vue'
// import TestComponent from './components/Test.vue'
import LgDashboard from './components/LgDashboard.vue'
import './index.css'

export default {
  name: 'App',
  components: {
    // DashboardComponent,
    LgDashboard
    // TestComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
