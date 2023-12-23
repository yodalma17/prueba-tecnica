<template>
  <section class="section-forms">
    <h2 class="title-form">
      {{ title }}
    </h2>
    <h3 class="subtitle-form" v-if="subtitle">
      {{ subtitle }}
    </h3>
    <div class="container-form-message" v-if="checkbox">
      <ul class="list-form">
        <li class="item-list" :class="{ 'active': active }" v-for="( {option, active}, index) in seletedCheckbox" :key="index" >
          <span class="text-option">{{ option }}</span>
          <span class="checkbox-custom" @click="functionSelectedCheckbox(option)" > <CheckSmall /> </span>          
        </li>
      </ul>
      <button class="btn-continue" @click="nextStep">
        Continuar
      </button>
    </div>
    <div class="container-form-message" v-else>
      <ul class="list-form">
        <li class="item-list" :class="[ selectedRadio === option && 'active' ]" v-for="(option, index) in options" :key="index" >
          <span class="text-option">{{ option }}</span>
          <span class="radio-custom" @click="functionSelectedRadio(option)"></span>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
  import CheckSmall from './icons/CheckSmall.vue'

  export default {
    name: 'FormsCustom',
    props: {
      title: {
        type: String,
        required: true
      },
      subtitle: {
        type: String
      },
      checkbox: {
        type: Boolean
      },
      options: {
        type: Array,
        required: true
      }

    },
    data() {
      return {
        selectedRadio: {
          type: String
        },
        seletedCheckbox: [],
      }
    },
    created() {
      if(this.checkbox) {
        this.seletedCheckbox = this.options.map( (option) => {
          return {option, active: false}
        })
      }
    },
    methods: {
      functionSelectedRadio( selected ) {
        this.selectedRadio = selected
        this.$emit('selection', selected)

        setTimeout(() => {
          this.$emit('selection', selected)
        }, 1500);
      },
      functionSelectedCheckbox( selected ) {
        const copy = this.seletedCheckbox
        copy.filter( item => item.option === selected )[0].active = !copy.filter( item => item.option === selected )[0].active
        this.seletedCheckbox = copy
      },
      nextStep() {
        this.$emit('selection', this.seletedCheckbox)

        setTimeout(() => {
          this.$emit('selection', this.seletedCheckbox)
        }, 1500);
      }
    },
    components: {
      CheckSmall
    }
  }
</script>

<style lang="sass">
  @import '../assets/global.sass'

  .section-forms
    padding: 16px 20px
    transition: all 0.5s
    .title-form
      margin: 0
      margin-bottom: 10px
      font-family: Fira Sans
      color: $colorDark
      font-size: 20px
      font-style: normal
      font-weight: 700
      line-height: normal
    .subtitle-form 
      color: #999
      font-size: 12px
      font-style: normal
      font-weight: 500
      line-height: normal
      margin: 0
      margin-bottom: 10px
    .container-form-message
      .list-form
        display: grid
        gap: 8px
        .item-list 
          border-radius: 15px
          opacity: 0.8
          background: $colorLight
          box-shadow: 2px 2px 8px 0px rgba(0, 0, 0, 0.25)
          padding: 0px 8px 0px 32px
          height: 48px
          transition: all 0.5s
          display: flex
          align-items: center
          .text-option 
            font-size: 14px
            font-style: normal
            font-weight: 700
            line-height: normal
          .radio-custom
            width: 20px
            height: 20px
            display: block
            border-radius: 50%
            border: 2px solid $colorDark
            margin-left: auto
            margin-right: 16px
            &:after
              content: ''
              margin: 4px
              transition: all 0.5s
              opacity: 0
          .checkbox-custom
            width: 20px
            height: 20px
            display: block
            border-radius: 5px
            position: relative
            border: 2px solid $colorDark
            margin-left: auto
            transition: all 0.5s
            margin-right: 16px
            svg 
              position: absolute
              left: -2px
              top: -1px
          &.active
            .radio-custom
              border-color: $colorPrimary
              &:after
                content: ''
                display: block
                width: 12px
                height: 12px
                border-radius: 50%
                background: $colorPrimary
                opacity: 1
                margin: 4px
            .checkbox-custom
              border-color: $colorPrimary
              background: $colorPrimary
      .btn-continue
        border-radius: 48px
        background: $colorPrimary
        color: $colorLight
        padding: 13px 39px
        font-size: 16px
        border: 0
        font-style: normal
        font-weight: 500
        line-height: normal
        box-shadow: 2px 2px 8px 0px rgba(0, 0, 0, 0.25)
        position: absolute
        bottom: 70px
        right: 20px
        transition: all 0.5s
        &:hover
          background: #4E19E2
  .hide
    .list-form
      .item-list:not(.active)
        height: 0
        overflow: hidden
    .container-form-message
      .btn-continue
        display: none
  .disabled
    height: 0
    overflow: hidden
    padding: 0
        
</style>