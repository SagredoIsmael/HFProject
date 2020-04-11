<template>
  <div class="container">
    <div class="tabs-container">
        <div class="tabs-item" @click="handleTabClick(tabNames.STATUS)" :class="{ 'tabs-item-active': activeTabName === tabNames.STATUS}">
            Status
        </div>        
        <div class="tabs-item" @click="handleTabClick(tabNames.RESULTS)" :class="{'tabs-item-active': activeTabName === tabNames.RESULTS}">
          Results
        </div>
        <div class="tabs-item" @click="handleTabClick(tabNames.MAINTENANCE)" :class="{'tabs-item-active': activeTabName === tabNames.MAINTENANCE}">
          Maintenance
        </div>              

    </div>
    <Component :is="currentTab"/> <!-- Directiva -->
  </div>
</template>

<script>
import Test from './components/Test.vue'
import Status from './components/Status.vue'
import Results from './components/Results.vue'
import Maintenance from './components/Maintenance.vue'

//JavaScript Variables
const tabNames = {
  STATUS: 'status',
  RESULTS: 'results',
  MAINTENANCE: 'maintenance'
}
//propiedades y variables de estado para llamarlas en css
export default {
  data: () => ({
    currentTab: null,
    activeTabName: null,
    tabNames,
    tabs: {
      [tabNames.STATUS]: Status,
      [tabNames.RESULTS]: Results,
      [tabNames.MAINTENANCE]: Maintenance,
    }
  }),
  components: {
    Test,
    Status,
    Results,
    Maintenance
  },
  methods:{
    handleTabClick: function(tabName){
      this.activeTabName = tabNames,
      this.currentTab = this.tabs[tabName];
    }
  }

}
</script>

<style>
.app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin: 0 auto;
}
.container{
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
}
.tabs-container{
  display: flex;
}
.tabs-item{
  padding: 8px;
  cursor: pointer;
}
.tabs-item-active,
.tabs-item:hover{
  background-color: blue;
  color:white;
  display: flex;
  text-align: center;
  table-layout: auto;
}
</style>
