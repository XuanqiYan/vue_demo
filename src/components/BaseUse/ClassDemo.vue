<template>
    <div>
        <p :class="{ black: isBlack, yellow: isYellow }">使用 class</p>
        <p :class="['black', yellow]">使用 class （数组）【 class名 , class 名】</p>
        <p :style="styleData">使用 style</p>
    </div>
</template>

<script>
/*
	动态属性写class style
	驼峰命名
*/
export default {
    data() {
        return {
            isBlack: false,
            isYellow: true,

            black: 'black',
            yellow: 'yellow',

            styleData: {
                fontSize: '40px', // 转换为驼峰式
                color: 'red',
                backgroundColor: '#ccc' // 转换为驼峰式
            }
        }
    }
}
</script>

<style scoped>
    .black {
        background-color: #999;
    }
    .yellow {
        color: yellow;
    }
</style>