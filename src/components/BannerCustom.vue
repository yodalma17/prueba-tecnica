<template>
  <section class="container-banner">
    <span class="title-top"> {{ topTitle }} </span>
    <h1 class="title-banner">
      {{ title }}
    </h1>
  </section>
</template>

<script>
  export default {
    name: 'BannerCustom',
    props: {
      topTitle: {
        type: String,
        required: true
      },
      title: {
        type: String,
        required: true
      },
    },
  }
</script>

<style lang="sass" scoped>
  @import '../assets/global.sass'

  .container-banner
    background: #8B62FF
    padding: 0 20px
    min-height: 102px
    border-radius: 16px
    margin: 0 20px
    gap: 10px
    transition: all 0.25s
    margin-bottom: 32px
    display: flex
    flex-direction: column
    justify-content: center
    .title-top
      color: $colorLight
      font-size: 20px
      font-style: normal
      font-weight: 300
      line-height: normal
    .title-banner
      color: $colorLight
      font-size: 30px
      font-style: normal
      font-weight: 700
      line-height: normal
      margin: 0
  .active
    transform: translateY(calc(50vh - 102px))
  .hide
    height: 0
    margin-bottom: 0
    min-height: 0
    overflow: hidden
</style>