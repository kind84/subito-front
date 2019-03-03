<template>
  <fieldset id="step_3" class="step" :disabled="disabled">
    <legend class="step_legend">Step 3</legend>
    <label class="step_label" for="rock">
      Are you ready to rock?
    </label>
    <input type="checkbox" id="rock" :value="true" v-model="rock">
    <input type="submit" id="submit_button" value="Complete Registration" :disabled="!rock">
  </fieldset>
</template>

<script>
export default {
  props: ["disabled"],
  data() {
    return{
      rock: false
    }
  }
}
</script>

<style>
#step_3  {
  background-color: rgb(255, 205, 159);
}

#submit_button {
  margin-top: 1rem;
}
</style>
