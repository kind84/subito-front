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
  position: relative;
}

#step_3:disabled::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  margin-top: 1.35rem;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.3);
}

#step_3 legend {
  position: relative;
  overflow: hidden;
}

#step_3:disabled legend::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.3);
}

@-moz-document url-prefix() {
  #step_3:disabled::before {
    content: "";
    position: absolute;
    top: -21.5px;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.3);
  }

  #step_3:disabled legend::before {
    content: "";
    position: absolute;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.3);
  }
}

#submit_button {
  margin-top: 1rem;
}
</style>
