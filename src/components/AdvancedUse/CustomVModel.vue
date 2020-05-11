<template>
    <input type="text"
        :value="text"
        @input="$emit('change', $event.target.value)"
    >
    <!--
        1. 上面的 input 使用了 :value 而不是 v-model
        2. 上面的 change1 和 model.event1 要对应起来
        3. text1 属性对应起来
    -->
</template>

<script>
export default {
    model: {
        prop: 'text', // 对应 props text1
        event: 'change'
    },
    props: {
        text: String,
        default() {
            return ''
        }
    }
}
</script>