<template>
    <option :value='option.value'>{{option.title}}</option>
</template>

<script>
export default {
    props: {
        option:{
            type: Object,
        }
    }
}
</script>

<style lang='sass' scoped>
    option
        margin-top: 5px
</style> 