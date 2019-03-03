<template>
  <fieldset id="step_3">
    <legend>Step 3</legend>
    <label for="rock">
      Are you ready to rock?
    </label>
    <input type="checkbox" id="rock" :value="true" v-model="rock">
    <input type="submit" id="submit_button" value="Complete Registration" :disabled="!rock">
  </fieldset>
</template>

<script>
export default {
  data() {
    return{
      rock: false
    }
  }
}
</script>
