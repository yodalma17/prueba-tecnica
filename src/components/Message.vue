<template>
  <section class="section-message" :class="{ 'active': open }">
    <div class="container-message">
      <LightBulb :active="show" />
      <div class="container-text" v-if="open">
        <p class="text-message" :class="{ 'show': show }"> {{ msg }} </p>
      </div>
    </div>
  </section>
</template>

<script>
  import LightBulb from './icons/LightBulb.vue'
  export default {
    name: 'MessageCustom',
    props: {
      msg: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        open: false,
        show: false
      }
    },
    created() {
      setTimeout(() => {
        this.open = true
        setTimeout(() => {
          this.show = true
        }, 500)
      }, 1000)
    },
    components: {
      LightBulb
    }
  }
</script>

<style lang="sass" scoped>
  @import '../assets/global.sass'
  .section-message 
    display: flex
    margin: 16px 0
    transition: all 0.5s
    .container-message
      background: $colorSecondary
      border-radius: 16px
      padding: 16px 8px
      margin: auto
      transition: all 0.5s
      width: 64px
      display: flex
      justify-content: center
      .container-text
        width: 0
        display: flex
        margin-left: 4px
        overflow: hidden
        .text-message 
          font-size: 14px
          margin: 0
          font-style: normal
          font-weight: 700
          min-width: 294px
          line-height: normal
          opacity: 0
          transition: all 0.5s
          color: #000
          &.show
            opacity: 1
    &.active
      padding: 0 20px 20px
      box-shadow: 2px 6px 8px -4px rgba(0, 0, 0, 0.25)
      margin: 0
      .container-message
        width: 100%
        .container-text
          width: 100%
  .disabled
    height: 0
    overflow: hidden
    margin: 0
    padding: 0 20px !important
</style>