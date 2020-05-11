<template>
    <div>
        <input v-model="name"/>
        <input v-model="info.demo.contry"/>
		<p>{{info.demo.contry}}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: 'xuanqiyan ',
            info: {
                city: '北京',
				demo:{
					contry:'中国'
				}
				
            }
        }
    },
    watch: {
        name(oldVal, val) {
          
            console.log('watch name', oldVal, val) // 值类型，可正常拿到 oldVal 和 val
        },
		//不是深度监听
		// info(oldVal,val){
		// 	console.log(val)
		// }	
		//引用类型需要深度监听  拿不到 oldVal 因为是引用类型拿的是指针
        info: {
            handler(oldVal, val) {
				console.log('####-->',oldVal) // oldVal实际上是info内部的指针 获取现在最新的info对象
                console.log('watch info') // 引用类型，拿不到 oldVal 。因为指针相同，此时已经指向了新的 val
				console.log(val)
            },
            deep: true // 开启深度监听
        }
    }
}
</script>