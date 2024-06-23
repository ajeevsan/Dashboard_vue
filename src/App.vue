<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <DashboardComponent/> -->
    <!-- <TestComponent/> -->
     <!-- <LgDashboard/> -->
      <UploadExcel/>     
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import DashboardComponent from './components/DashboardComponent.vue'
// import TestComponent from './components/Test.vue'
// import IssueDashboard from './components/IssueDashboard.vue'
// import LgDashboard from './components/LgDashboard.vue'
import UploadExcel from './components/UploadExcel.vue'

import './index.css'

export default {
  name: 'App',
  components: {
    // DashboardComponent,
    // LgDashboard,
    UploadExcel
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
