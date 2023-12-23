<template>
  <section class="container-form">
    <h2 class="title-form">
      {{ title }}
    </h2>
    <div class="container-input">
      <input v-autofocus type="number" class="input-form" placeholder="Teléfono" v-model="numberInput"/>
      <button class="btn-finish">
        Finalizar
      </button>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'FormNumber',
    props: {
      title: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        numberInput: {
          type: Number
        }
      }
    },
    directives: {
      autofocus: {
        // La función de enlace se llama cuando se inserta el elemento en el DOM
        mounted(el) {
          el.focus();
        },
      },
    },
  }
</script>

<style lang="sass" scoped>
  @import '../assets/global.sass'

  .container-form
    padding: 16px 20px
    .title-form
      font-family: Fira Sans
      font-size: 20px
      color: #000
      font-style: normal
      font-weight: 700
      line-height: normal
    .container-input 
      position: relative
      .input-form
        border-radius: 24px
        border: 1.5px solid #8B62FF
        padding: 12px 32px
        background: #FFF
        color: rgba(26, 26, 26, 1)
        font-size: 16px
        font-style: normal
        font-weight: 300
        line-height: normal
        width: 100%
        box-sizing: border-box
        padding-right: 130px
        &::placeholder
          color: rgba(26, 26, 26, 0.25)
      .btn-finish 
        border-radius: 24px
        padding: 12px 32px
        background: $colorPrimary
        font-size: 16px
        font-style: normal
        font-weight: 700
        line-height: normal
        border: 0  
        height: 100%
        color: $colorLight
        position: absolute
        right: 0
</style>