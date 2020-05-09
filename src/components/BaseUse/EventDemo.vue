<template>
    <div>
        <p>{{num}}</p>
        <button @click="increment1">+1</button>
        <button @click="increment2(2, $event)">+2</button>
    </div>
	<div>
		<!-- 阻止单机事件继续传播-->
		<a v-on:click.stop='doThis' ></a>
		<!-- 阻止表单提交 -->
		<from v-on:click.pervent='doThis' ></from>
		<!-- 修饰符可以串联 -->
		<from v-on:click.stop.pervent='doThis' ></from>
		<!-- 事件捕获模式 即内部元素触发的事件先在此处处理 然后在执行内部元素的处理-->
		<div v-on:click.capture='doThis'>
		<!-- 事件不是内部元素触发的 -->	
		<div v-on:click.self='doThis'>	
		
		<!-- Alt和 Shift和ctrl 一起被按下 -->
		<div @click.ctrl='toThis'>
		<!--只按ctrl 键 -->
		<div @click.ctrl.exact='toThis'>	
		<!-- 没有任何系统修饰符被按下才触发-->
		<div @click.exact='toThis'>
	</div>
</template>

<script>
/*
	event 参数 和自定义参数 
	事件修饰符和按键修饰符	
   观察事件被绑定到哪里 ？
*/	
export default {
    data() {
        return {
            num: 0
        }
    },
    methods: {
        increment1(event) {
            // 1.是原生的 event 对象，没有经过任何装饰
            console.log('event', event, event.__proto__.constructor)
			//2. 事件在哪个元素上监听的？
            console.log(event.target)
			//3. 事件在哪个元素上触发的？
            console.log(event.currentTarget) // 注意，事件是被注册到当前元素的，和 React 不一样
            this.num++

            // 1. event 是原生的
            // 2. 事件被挂载到当前元素
        },
        increment2(val, event) {
            console.log(event.target)
            this.num = this.num + val
        },
        loadHandler() {
            // do some thing
        }
    },
    mounted() {
        window.addEventListener('load', this.loadHandler)
    },
    beforeDestroy() {
        //【注意】用 vue 绑定的事件，组建销毁时会自动被解绑
        // 自己绑定的事件，需要自己销毁！！！
        window.removeEventListener('load', this.loadHandler)
    }
}
</script>