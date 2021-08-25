<template>
    <transition name="fade">
        <div class="box" v-if="show">
            <div class="block">
                <p>Новый клиент успешно создан</p>
            </div>
        </div>
    </transition>
</template>

<script>


export default{
    props: {
        show:{
            type: Boolean,
        }
    }
}
</script>

<style lang='sass' scoped>
    .box
        display: flex
        justify-content: space-around
    .block
        position: fixed
        width: 300px
        text-align: center
        border: 3px solid #00D1FF
        background-color: rgba(255, 255, 255, 0.9)
        box-sizing: border-box
        padding: 20px 15px
        margin: 0 auto
        top: 45%
        font-size: 18px
        font-weight: bold
        text-transform: uppercase
        border-radius: 20px
        letter-spacing: 1.5px
        line-height: 30px
        


</style>