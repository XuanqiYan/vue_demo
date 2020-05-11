<template>
    <div>
        <Input @add="addHandler"/>
        <List :list="list" @delete="deleteHandler"/>
    </div>
</template>

<script>
import Input from './Input'
import List from './List'
/*
	组件通信考点：
		props 和 $emit
			vue中父组件使用props 传递数据给子组件 ，子组建使用事件的$emit传递参数给父组件 
			
		非父子组件传值
			vuex
			自定义事件 ：（bus/总线机制）  vue原型上添加了一个自定义属性，属性的值就是 空的vue实例
				核心：
				两个组件使用 同一个共同的vue实例 实现
				一个组件 在vue实例上触发 自定义事件
				另一个组件 通过vue实例监听 自定义事件 ，注意 该组件在结束之前必须要通过$off 方式手动消除自定义事件的绑定，否则就是内存泄漏 
				
		组件生命周期 的函数和执行顺序  和 父子组件生命周期调用顺序 
*/
export default {
    components: {
        Input,
        List
    },
    data() {
        return {
            list: [
                {
                    id: 'id-1',
                    title: '标题1'
                },
                {
                    id: 'id-2',
                    title: '标题2'
                }
            ]
        }
    },
    methods: {
        addHandler(title) {
            this.list.push({
                id: `id-${Date.now()}`,
                title
            })
        },
        deleteHandler(id) {
            this.list = this.list.filter(item => item.id !== id)
        }
    },
    created() {
        // vue实例在内存中创建模型
        console.log('index created')
    },
    mounted() {
         // vue 实例在网页上渲染完成，大部分操作需要在这里处理 ajax获取信息 /绑定事件等
        console.log('index mounted')
    },
    beforeUpdate() {
       
        console.log('index before update')
    },
    updated() {
        // eslint-disable-next-line
        console.log('index updated')
    },
}
</script>