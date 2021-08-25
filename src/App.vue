<template>
  <div class="container">
    <Form />
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    Form
  }
}
</script>

<style lang='sass'>
  body
    font-family: Arial
    margin: 0
    background-image: url(./img/background.jpeg)
    background-repeat: repeat
    background-size: cover 

  .container
    box-sizing: border-box
    max-width: 1200px
    margin: 20px auto
    background-color: #fff
    min-height: 900px
    border-radius: 35px
    border: 3px solid #00D1FF
    padding: 20px 160px

    @media all and (max-width: 1366px)
      padding: 55px 70px
      max-width: 700px
    
    @media all and (max-width: 768px)
      padding: 40px 20px
      max-width: 600px
    
    @media all and (max-width: 414px)
      max-width: 90%

</style>
