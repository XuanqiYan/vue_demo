<template>
    <div>
        <p>vue 高级特性</p>
        <hr>

        <!-- 自定义 v-model -->
        <!-- <p>{{name}}</p> -->
        <!-- <CustomVModel v-model="name"/> -->

        <!-- nextTick -->
        <!-- <NextTick/> -->

        <!-- slot -->
     <!--  <SlotDemo :url="website.url">
            <i>{{website.title}}</i>
        </SlotDemo> -->
		
		<!-- 作用域插槽 父组件定义插槽模版的时候可能使用子组件的数据-->
     <!--  <ScopedSlotDemo >
			<template v-slot="xxx">
				{{website.title}}
				{{xxx.ooo.title}} 
			</template>
		
        </ScopedSlotDemo> -->

        <!-- 动态组件 -->
        <!-- <component :is="'NextTick'"/> -->
        
        <!-- 异步组件 动态路由 -->
        <FormDemo v-if="showFormDemo"/>
        <button @click="showFormDemo = true">show form demo</button>
			
		

        <!-- keep-alive -->
        <!-- <KeepAlive/> -->

        <!-- mixin -->
        <!-- <MixinDemo/> -->
    </div>
</template>

<script>
import CustomVModel from './CustomVModel'
import NextTick from './NextTick'
import SlotDemo from './SlotDemo'
import ScopedSlotDemo from './ScopedSlotDemo'
// import KeepAlive from './KeepAlive'
// import MixinDemo from './MixinDemo'

/*
	import User from 'User'
	动态路由
	{
		path:'/user/:id',
		component: User
	}
		
*/
export default {
	
    components: {
        CustomVModel,
        NextTick,
        SlotDemo,
        ScopedSlotDemo,
        FormDemo: () => import('../BaseUse/FormDemo'),
        // KeepAlive
        // MixinDemo
    },
    data() {
        return {
			c:'NextTick',	
            name: 'xuanqiyan',
            website: {
                url: 'xuanqiyan.com',
                title: 'xuanqiyan',
                subTitle: 'mianshi...'
            },
            // NextTickName: "NextTick",
            showFormDemo: false
        }
    }
}
</script>