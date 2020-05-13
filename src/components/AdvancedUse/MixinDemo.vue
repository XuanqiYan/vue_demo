<template>
    <div>
        <p>{{name}} {{major}} {{city}}</p>
        <button @click="showName">显示姓名</button>
    </div>
</template>

<script>
/*
	1. 将组件的公共逻辑抽离出来
		注意：
			对于data 和 methods 来说 如果组件和 minxi 重复了 ，以当前组件来生效的 
			对于生命周期钩子来说，即使重复了，不会覆盖 ，而是先执行minxi的生命周期，再执行组件的生命周期 
	2. 有点缺陷，但是能用
		minxi 变量原来不明，不利阅读
		多个minxi 内部属性和方法可能命名重冲突
		minxi 和组件可能出现 多对多关系，比较复杂
	3. vue3.0提出compositions API 解决 minxi的缺陷问题 
	
*/	
import myMixin from './mixin'
import myMixin1 from './mixin1.js'

export default {
    mixins: [myMixin1,myMixin], // 可以添加多个，会自动合并起来  ，myMixin会覆盖myMixin1
    data() {
        return {
            name: 'xuanqiyan',
            major: 'web 前端',
		
        }
    },
    methods: {
	
    },
    mounted() {
        console.log('component mounted', this.name)
    }
}
</script>