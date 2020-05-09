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