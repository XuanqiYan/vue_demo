<template>
    <div>
        <p>遍历数组</p>
        <ul>
            <li v-for="(item, index) in listArr" :key="item.id">
                {{index}} - {{item.id}} - {{item.title}}
            </li>
        </ul>

        <p>遍历对象</p>
        <ul   v-if='flag' >  
            <li v-for="(val, key, index) in listObj" :key="val.id"> 
			
                {{index}} - {{key}} -  {{val.title}}
            </li>
        </ul>
    </div>
</template>

<script>
	/*
		如何遍历对象
		key的重要性 (key不能乱写 如random  index  和实体相关的值 如 Id)
		v-for 和 v-if 最好不要 一起使用
			因为： v-for运算级别比v-if高  ，可能造成性能浪费
	*/
export default {
    data() {
        return {
            flag: false,
            listArr: [
                { id: 'a', title: '标题1' }, // 数据结构中，最好有 id ，方便使用 key
                { id: 'b', title: '标题2' },
                { id: 'c', title: '标题3' }
            ],
            listObj: {
                a: { id:1, title: '标题1' },
                b: { id:2, title: '标题2' },
                c: { id:3, title: '标题3' },
            }
        }
    }
}
</script>