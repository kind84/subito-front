<template>
  <div id="app" :key=clear>
    <div id="page-wrap">
      <h1 class="main-title">Seminar <span class="main-title__span">Registration</span></h1>
      <form class="main-form" @submit.prevent="complete3">
        <StepOne @complete1="complete1 = $event" />
        <StepTwo :disabled="!complete1" @complete2="complete2 = $event"/>
        <StepThree :disabled="!complete2" />
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
* {
  box-sizing: border-box;
}

html {
  height: 100%;
}

body {
  margin: 0;
  height: 100%;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background: radial-gradient(circle at top, gray, rgb(71, 71, 71), rgb(53, 53, 53) 50%);
  height: 100%;
  margin: 0;
  position: fixed;
}

#page-wrap {
  padding: 1rem;
}

.main-title {
  font-size: 3rem;
  margin-top: 0;
  color: white;
}

.main-title__span {
  color: rgb(83, 143, 255);
}

.main-form {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}

.step {
  border: none;
  padding: 1rem;
  align-self: start;
}

fieldset:disabled {
  opacity: 10%;
}

.step_legend {
  border-radius: 0.8rem;
  background-color: white;
  padding: 0.5rem;
  font-size: 1.5rem;
  font-weight: bold;
  color: black;
}

.step_label {
  font-style: italic;
  font-size: 1.5rem;
  font-family: serif;
}

.step_label__small {
  font-size: 1rem;
}

.text-field_wrap {
  display: flex;
  flex-direction: row;
  align-items: flex-end;
  margin: 0.5rem 0;
}

.text-field_input {
  margin: 0 0.4rem;
}

.step_completed {
  display: block;
  margin: auto;
  max-height: 9rem;
}
</style>
