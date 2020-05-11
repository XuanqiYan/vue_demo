<template>
    <div>
        <p>num {{num}}</p>
        <p>double1 {{double1}}</p>
        <input v-model="double2"/>
		<p @click='changeAge'>{{age}}</p>
		
    </div>
</template>

<script>
/*
	1.计算属性使用缓存  ：只要依赖的变量不发生改变 组件在次渲染的时候 对于计算属性会使用上一次组件的计算的结果 
	
	2.v-model 绑定的计算属性 :需要设置 setter
*/
export default {
    data() {
        return {
            num: 20,
			age:22
        }
    },
    computed: {
        double1() {
			console.log('计算了一次')
            return this.num * 2
        },
		//
        double2: {
            get() {
                return this.num * 2
            },
			set(val){
				return val/2
			}
        }
    },
	methods:{
		changeAge(){
			this.age=30
		}
	}
}
</script>