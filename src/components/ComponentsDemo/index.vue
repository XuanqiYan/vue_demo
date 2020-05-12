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
	组件通信3种方式 ：
		1.props 和 $emit
			vue中父组件使用props 传递数据给子组件 ，子组建使用事件的$emit传递参数给父组件 
			
		2.非父子组件传值
			
			自定义事件 ：（bus/总线机制）  vue原型上添加了一个自定义属性，属性的值就是 空的vue实例
				核心：
				两个组件使用 同一个共同的vue实例 实现
				一个组件 在vue实例上触发 自定义事件
				另一个组件 通过vue实例监听 自定义事件 ，注意 该组件在结束之前必须要通过$off 方式手动消除自定义事件的绑定，否则就是内存泄漏 
		
		3. vuex
				
	组件生命周期 的函数和执行顺序 
		挂载
			created
				vue实例在created之后会在内存种形成一个可用vue实例对象，这个对象在created钩子之前，
				会在实例对象上注册一些data数据，以及做一些事件绑定和一些校验工作 
				并没有参与dom结构的渲染 等工作
			mounted	
				mounted执行之后已经完了dom结构的渲染和挂载到网页的工作
				在mounted 之前，根据内存种的处理的vue实例对象，在结合指定dom模版的通过render的渲染函数，根据vue的相关模版指令将模版和数据结合
				
		跟新
			由于vue是 mvvm 根绝data的变化 视图就要跟新 
			updated
		销毁
			beforedistory 在销毁整个vue实例之前需要做什么？
				
			手动解除 vue对象种对dom的事件绑定 
			
	父子组件生命周期调用顺序 	
		index created
		list created
		list mounted
		index mounted
		
		index before update
		list before update
		list updated
		index updated
		
		index before distory
		list before distory
		list distory
		index distory
	
	总结：先内部子组件执行相关生命周期，然后才是父组件执行相关生命周期		
		
		
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
        // vue实例在内存中创建模型对象
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
  
        console.log('index updated')
    },
}
</script>