<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

    <!-- <TplDemo/> -->
    <!-- <ConditionDemo/> -->
    <!-- <EventDemo/> -->
	<!-- <ComputedDemo/> -->
    <ComponentDemo/>

    <!-- <AdvancedUse/> -->
	<!-- <Todo/> -->

    <!-- <CartDemo/> -->
	<!-- <WatchDemo /> -->
	<!-- <ListDemo /> -->
	<!-- <FormDemo /> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

 import TplDemo from './components/BaseUse/TplDemo'
// import ConditionDemo from './components/BaseUse/ConditionDemo'
import EventDemo from './components/BaseUse/EventDemo'

import ComponentDemo from './components/ComponentsDemo/index'

// import AdvancedUse from './components/AdvancedUse/index'
import Todo from './components/BaseUse/Todo.vue'
import CartDemo from './components/Cart/index'
import ComputedDemo from './components/BaseUse/ComputedDemo.vue'
import WatchDemo from './components/BaseUse/WatchDemo.vue'
import ListDemo from './components/BaseUse/ListDemo.vue'
import FormDemo from './components/BaseUse/FormDemo.vue'
 
export default {
  name: 'app',
  components: {
	WatchDemo,  
	ComputedDemo, 
	TplDemo,
	ListDemo,
	FormDemo,
    // HelloWorld
    EventDemo,
    ComponentDemo
    // AdvancedUse
   // CartDemo,
	//Todo
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
