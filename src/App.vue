<template>
  <HeaderBar 
    title="Progreso" 
    :percentage="percentage"
  />
  <div class="container">
    <BannerCustom
      topTitle="Oferta del mes" 
      title="Ahorra un 50%"
      :class="{ 'active': step === 1, 'hide': step > 3}"
    />
		<Transition name="slide-up">
      <Forms 
        title="Pregunta 1"
        :options="['Option 1', 'Option 2', 'Option 3' ]"
        @selection="setOptions"
        v-if="step >= 2"
        :class="{ 'hide': step >= 3, 'disabled': step === 6}"
      />
    </Transition>
    <Message
        v-if="step >= 3"
        :class="{ 'disabled': step === 6}"
        msg="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed quis risus eget urna mollis ornare. Sed quis risus eget urna mollis ornare."
      />
    <Transition name="slide-up">  
      <Forms 
        title="Pregunta 2"
        :checkbox="true"
        @selection="setOptionsCheckbox"
        :options="['Option 1', 'Option 2', 'Option 3', 'Option 4' ]"
        v-if="step >= 3"
        :class="{ 'hide': step >= 6}"
      />
    </Transition>
    <Message
        v-if="step >= 5"
        msg="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed quis risus eget urna mollis ornare. Sed quis risus eget urna mollis ornare."
      />
    <FormNumber 
      title="Guarda tus respuestas"
      v-if="step >= 6"
    />
  </div>
</template>

<script>
  import HeaderBar from '@/components/HeaderBar.vue'
  import BannerCustom from '@/components/BannerCustom.vue'
  import Forms from '@/components/Forms.vue'
  import FormNumber from '@/components/FormNumber.vue'
  import Message from '@/components/Message.vue'

  export default {
    name: 'App',
    data() {
      return {
        percentage: (100 / 6 ),
        step: 1,
        data: {responseRadio: '', responseCheckbox: [], responseNumber: ''}
      }
    },
    mounted() {
      setTimeout(() => {
        this.step += 1
        this.setPercentage()
      }, 2000)
    },
    methods: {
      setPercentage() {
        this.percentage = (100 / 6 ) * this.step
      },
      setStep() {
        this.step += 1
        this.setPercentage()
      },
      setOptions(selected) {
        this.data.responseRadio = selected
        this.setStep()
      },
      setOptionsCheckbox(selected) {
        this.data.responseCheckbox = selected
        this.setStep()
      }
    },
    components: {
      HeaderBar,
      BannerCustom,
      Forms,
      FormNumber,
      Message
    }
  }
</script>

<style lang="sass">
  @import url('https://fonts.googleapis.com/css2?family=Fira+Sans:wght@300;500;700&display=swap')
  @import './assets/global.sass'

  body
    margin: 0
    padding: 0
    overflow: hidden
    #app
      font-family: 'Fira Sans', sans-serif
      -webkit-font-smoothing: antialiased
      -moz-osx-font-smoothing: grayscale
      color: #2c3e50
    .container 
      max-width: 1440px
      height: calc(100vh - 43px)
      margin-top: -43px
      padding-top: 50px
      display: flex
      flex-direction: column
      position: relative
      &::after
        content: ""
        position: absolute
        bottom: 0
        width: 100%
        background: #fff
        box-shadow: 3px 2px 73px 50px rgb(255 255 255 / 82%)
    ul 
      padding: 0
      margin: 0
      list-style: none
</style>
