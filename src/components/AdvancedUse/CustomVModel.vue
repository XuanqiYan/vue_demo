<template>
    <input type="text"
        :value="text"
        @input="$emit('change', $event.target.value)"
    >
    <!--
        1. 上面的 input 使用了 :value 而不是 v-model
        2. 上面的 change和 model.event 要对应起来
        3. 上面text 和 model.prop 属性对应起来
    -->
</template>

<script>
export default {
    model: {
        prop: 'text',
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