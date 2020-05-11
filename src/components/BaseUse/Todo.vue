<template>
  <div id="app">
    <p @click="changeName">{{list}}</p>
    <ul>
        <li v-for="(item, index) in list" :key="index">
            {{item}}
        </li>
    </ul>
    <button @click="addItem">添加一项</button>
  </div>
</template>

<script>
/*
	插值表达式 
*/	
	
export default {
  name: 'app',
  /*
	为什么 子组建定义data 需要用function 因为 组件可能会被多次使用，但是每次使用组件的数据应该相互独立的 ，为了达到这目的使用函数函数返回对象
  */
  data() {
      return {
        name: 'vue',
        list: ['a', 'b', 'c']
      }
  },
  methods: {
    changeName() {
        this.name = 'xuanqiyan'
    },
    addItem() {
        this.list.push(`${Date.now()}`)
    }
  }
}
</script>

