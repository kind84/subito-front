<template>
  <fieldset id="step_2" class="step" :disabled="disabled">
    <legend class="step_legend">Step 2</legend>
    <div class="radio_input">
      <p class="step_label step2_label">
        Would you like your company name on your badges?
      </p>
      <input 
        type="radio" 
        id="company_name_toggle_on" 
        name="company_name_toggle_group" 
        :value="true" 
        v-model="needCompany"
        @change="complete[1] = false">
      <label class="step_label" for="company_name_toggle_on">Yes</label>
      &emsp;
      <input 
        type="radio" 
        id="company_name_toggle_off" 
        name="company_name_toggle_group" 
        :value="false" 
        v-model="needCompany"
        @change="complete[1] = true">
      <label class="step_label" for="company_name_toggle_off">No</label>
      <div class="text-field_wrap" id="company_name_wrap" v-if="needCompany">
        <label class="step_label step_label__small" for="company_name">
          Company Name:
        </label>
        <input class="text-field_input" type="text" id="company_name" v-model="compName">
      </div>
    </div>
    <div class="radio_input">
      <p class="step_label step2_label">
        Will anyone in your group require special accommodations?
      </p>
      <input 
        type="radio" 
        id="special_accommodations_toggle_on" 
        name="special_accommodations_toggle"
        :value="true" 
        v-model="needSpecial"
        @change="complete[2] = false">
      <label class="step_label" for="special_accommodations_toggle_on">Yes</label>
      &emsp;
      <input 
        type="radio" 
        id="special_accommodations_toggle_off" 
        name="special_accommodations_toggle"
        :value="false" 
        v-model="needSpecial"
        @change="complete[2] = true">
      <label class="step_label" for="special_accommodations_toggle_off">No</label>
      <div class="text-field_wrap" id="special_accommodations_wrap" v-if="needSpecial">
        <label class="step_label step_label__small" for="special_accomodations_text">
          Please explain below:
        </label>
        <textarea rows="10" cols="10" id="special_accomodations_text" v-model="special"></textarea>
      </div>  
    </div>
    <transition name="slide" mode="out-in">
      <img class="step_completed" v-if="complete[1] && complete[2]" src="../assets/done.png" alt="Done" />
    </transition>
  </fieldset>
</template>

<script>
export default {
  props: ["disabled"],
  data() {
    return {
      needCompany: "",
      compName: "",
      needSpecial: "",
      special: "",
      complete: {1:false, 2:false}
    }
  },
  watch: {
    needCompany() {
      if (!this.needCompany) {
        this.compName = ""
      }
    },
    compName() {
      this.compName !== "" ? this.complete[1] = true : this.complete[1] = false
    },
    needSpecial() {
      if (!this.needSpecial) {
        this.special = ""
      }
    },
    special() {
      this.special !== "" ? this.complete[2] = true : this.complete[2] = false
    },
    complete: {
      handler() {
        if (this.complete[1] && this.complete[2]) {
          this.$emit("complete2", true)
        } else {
          this.$emit("complete2", false)
        }
      },
      deep: true
    }
  }
}
</script>

<style>
#step_2 {
  background-color: lightblue;
  position: relative;
}

#step_2:disabled::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  margin-top: 1.35rem;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.3);
}

#step_2 legend {
  position: relative;
  overflow: hidden;
}

#step_2:disabled legend::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.3);
}

@-moz-document url-prefix() {
  #step_2:disabled::before {
    content: "";
    position: absolute;
    top: -21.5px;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.3);
  }

  #step_2:disabled legend::before {
    content: "";
    position: absolute;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.3);
  }
}

.step2_label {
  margin: 0.5rem 0;
}

.radio_input {
  margin-bottom: 1.5rem;
}

#special_accommodations_wrap {
  flex-direction: column;
  align-items: flex-start;
}

#special_accomodations_text {
  margin-top: 0.5rem;
  width: 100%;
  max-height: 6rem;
}
</style>

