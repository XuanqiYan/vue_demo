<template>
    <div>
        <button @click="changeState('A')">A</button>
        <button @click="changeState('B')">B</button>
        <button @click="changeState('C')">C</button>

       <keep-alive><!-- tab 切换 -->
            <KeepAliveStageA v-if="state === 'A'"/> <!-- v-show -->
            <KeepAliveStageB v-if="state === 'B'"/>
            <KeepAliveStageC v-if="state === 'C'"/>
        </keep-alive>
    </div>
</template>

<script>
	
/*
	keep-alive 做组件的静态缓存的
		1.内部的组件在第一次渲染完毕后，keep-alive 能将 组件的模板缓存到内存中 
		2.下次在渲染该组件的时候就不需要执行组件的渲染流程（复杂的生命周期，也不会执行data运算..）而是直接获取内存的缓存好的静态模板
		3.对项目的渲染性能有很大提升	
		
*/	
import KeepAliveStageA from './KeepAliveStateA'
import KeepAliveStageB from './KeepAliveStateB'
import KeepAliveStageC from './KeepAliveStateC'

export default {
    components: {
        KeepAliveStageA,
        KeepAliveStageB,
        KeepAliveStageC
    },
    data() {
        return {
            state: 'A'
        }
    },
    methods: {
        changeState(state) {
            this.state = state
        }
    }
}
</script>