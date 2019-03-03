<template>
  <div id="app">
    <div id="page-wrap">
      <h1>Seminar <span>Registration</span></h1>
      <form @submit.prevent="complete3">
        <StepOne @complete1="complete1 = $event" :key="clear" />
        <StepTwo v-if="complete1" @complete2="complete2 = $event" />
        <StepThree v-if="complete2"/>
      </form>
    </div>
  </div>
</template>

<script>
import StepOne from './components/StepOne.vue'
import StepTwo from './components/StepTwo.vue'
import StepThree from './components/StepThree.vue'

export default {
  name: 'app',
  components: {
    StepOne,
    StepTwo,
    StepThree
  },
  data() {
    return {
      complete1: false,
      complete2: false,
      clear: false
    }
  },
  methods: {
    complete3() {
      this.complete1 = false,
      this.complete2 = false,
      this.clear = !this.clear
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
