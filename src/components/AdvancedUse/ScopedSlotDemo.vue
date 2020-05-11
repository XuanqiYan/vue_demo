<template>
    <a :href="url">
        <slot :ooo="website">
            
        </slot>
    </a>
</template>

<script>
export default {
    props: ['url'],
    data() {
        return {
            website: {
                url: 'http://baidu.com/',
                title: 'baidu',
                subTitle: '百度'
            }
        }
    }
}
</script>