<template>
    <div>
        <input v-model="name"/>
        <input v-model="info.city"/>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: 'xuanqiyan ',
            info: {
                city: '北京'
            }
        }
    },
    watch: {
        name(oldVal, val) {
          
            console.log('watch name', oldVal, val) // 值类型，可正常拿到 oldVal 和 val
        },
		//引用类型需要深度监听  拿不到 oldVal  因为是引用类型拿的是指针
        info: {
			
            handler(oldVal, val) {
               
                console.log('watch info', oldVal, val) // 引用类型，拿不到 oldVal 。因为指针相同，此时已经指向了新的 val
            },
            deep: true // 深度监听
        }
    }
}
</script>