<template>
    <div>
        <p>vue 高级特性</p>
        <hr>

        <!-- 自定义 v-model -->
        <p>{{name}}</p>
        <CustomVModel v-model="name"/> 

        <!-- nextTick -->
        <NextTick/>

        <!-- slot -->
        <SlotDemo :url="website.url">
			<!-- 父组件传递 自身的数据到子组建-->
            {{website.title}}
        </SlotDemo>
		
        <ScopedSlotDemo :url="website.url">
			<!--父组件传递的是子组件的数据 -->
            <template v-slot="xxx">
                {{xxx.ooo.title}}
            </template>
        </ScopedSlotDemo>

        <!-- 动态组件 -->
        <!-- <component :is="NextTickName"/> -->
        
        <!-- 异步组件 -->
        <!-- <FormDemo v-if="showFormDemo"/>
        <button @click="showFormDemo = true">show form demo</button> -->

        <!-- keep-alive -->
        <!-- <KeepAlive/> -->

        <!-- mixin -->
        <MixinDemo/>
    </div>
</template>

<script>
import CustomVModel from './CustomVModel'
import NextTick from './NextTick'
import SlotDemo from './SlotDemo'
import ScopedSlotDemo from './ScopedSlotDemo'
// import KeepAlive from './KeepAlive'
// import MixinDemo from './MixinDemo'

export default {
    components: {
        CustomVModel
        NextTick
        SlotDemo,
        ScopedSlotDemo,
        // FormDemo: () => import('../BaseUse/FormDemo'),
        // KeepAlive
        // MixinDemo
    },
    data() {
        return {
            name: 'xuanqiyan',
            website: {
                url: 'xuanqiyan.com',
                title: 'xuanqiyan',
                subTitle: 'mianshi...'
            },
            // NextTickName: "NextTick",
            // showFormDemo: false
        }
    }
}
</script>