<template>
    <a >
        <slot :ooo="website">
            
        </slot>
    </a>
</template>

<script>
export default {
 
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