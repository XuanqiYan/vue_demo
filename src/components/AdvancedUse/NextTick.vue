<template>
  <div id="app">
    <ul ref="ul1">
        <li v-for="(item, index) in list" :key="index">
            {{item}}
        </li>
    </ul>
    <button @click="addItem">添加一项</button>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
      return {
        list: ['a', 'b', 'c']
      }
  },
  methods: {
    addItem() {
        this.list.push(`${Date.now()}`)
        this.list.push(`${Date.now()}`)
        this.list.push(`${Date.now()}`)
		
		
		const ulElem = this.$refs.ul1
		
		console.log( ulElem.childNodes.length )

        /* 1. 异步渲染，data改变后dom不会立即渲染 ，dom 的渲染是一个异步过程
		   2. 待 DOM 异步渲染完再执行$nextTick回调 
           3. 页面渲染时会将 data 的修改做整合，多次 data修改只会渲染一次，提高性能
				push 了3次 但是执行nextTick 只执行一次
		*/	  
        this.$nextTick(() => {
          const ulElem = this.$refs.ul1
          console.log( ulElem.childNodes.length )
        })
    }
  }
}
</script>

