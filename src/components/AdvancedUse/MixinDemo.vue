<template>
    <div>
        <p>{{name}} {{major}} {{city}}</p>
        <button @click="showName">显示姓名</button>
    </div>
</template>

<script>
/*
	1. 将组件的公共逻辑抽离出来
	2. 有点缺陷，但是能用
		 minxi 变量原来不明，不利阅读
		多个minxi 内部属性和防范可能命名重冲突
		minxi 和组件可能出现 多对多关系，比较复杂
	3. vue3提出compositions API 解决 minxi的缺陷问题 
*/	
import myMixin from './mixin'

export default {
    mixins: [myMixin], // 可以添加多个，会自动合并起来
    data() {
        return {
            name: 'xuanqiyan',
            major: 'web 前端'
        }
    },
    methods: {
    },
    mounted() {
       
        console.log('component mounted', this.name)
    }
}
</script>