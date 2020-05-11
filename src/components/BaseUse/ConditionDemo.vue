<template>
    <div>
        <p v-if="type === 'a'">A</p>
        <p v-else-if="type === 'b'">B</p>
        <p v-else>other</p>

        <p v-show="type === 'a'">A by v-show</p>
        <p v-show="type === 'b'">B by v-show</p>
    </div>
</template>

<script>
/*
	v-if 和 v-show 区别 ？
		v-if 根据条件从dom结构中创建和删除 节点
		v-show 根据条件从dom结构中隐藏和显示 节点
	如何选择？
		跟新频繁 v-show 不频繁 v-if
*/	
export default {
    data() {
        return {
            type: 'a'
        }
    }
}
</script>