<template>
  <header class="header-bar">
    <span class="title-bar"> {{ title }} </span>
    <div class="container-bar"><span class="bar" :style="styleBar"></span></div>
  </header>
</template>

<script>
  export default {
    name: 'HeaderBar',
    props: {
      title: {
        type: String,
        required: true
      },
      percentage: {
        type: Number,
        default: 0,
        validator (value) {
          return value >= 0 && value <= 100
        }
      }
    },
    data() {
      return {
        styleBar: {
          width: `${this.percentage}%`,
        },
      }
    },
    watch: {
      percentage() {
        this.styleBar.width = `${this.percentage}%`
      }
    }
  }
</script>

<style lang="sass" scoped>
  @import '../assets/global.sass'

  .header-bar
    padding: 8px 20px
    background: $colorLight
    box-shadow: 0px 8px 8px 0px rgba(0, 0, 0, 0.10)
    .title-bar
      color: #000
      font-size: 12px
      font-style: normal
      font-weight: 300
      line-height: normal
      margin-bottom: 4px
    .container-bar
      border-radius: 16px
      width: 100%
      height: 8px
      background: rgb(139 98 255 / 10%)
    .bar
      border-radius: 16px
      background: $colorPrimary
      display: block
      width: 30%
      height: 100%
      transition: all 0.5s
</style>