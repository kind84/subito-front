<template>
  <fieldset id="step_2">
    <legend>Step 2</legend>
    <p>
      Would you like your company name on your badges?
    </p>
    <input 
      type="radio" 
      id="company_name_toggle_on" 
      name="company_name_toggle_group" 
      :value="true" 
      v-model="needCompany"
      @change="complete[1] = false">
    <label for="company_name_toggle_on">Yes</label>
    &emsp;
    <input 
      type="radio" 
      id="company_name_toggle_off" 
      name="company_name_toggle_group" 
      :value="false" 
      v-model="needCompany"
      @change="complete[1] = true">
    <label for="company_name_toggle_off">No</label>
    <div id="company_name_wrap" v-if="needCompany">
      <label for="company_name">
        Company Name:
      </label>
      <input type="text" id="company_name" v-model="compName">
    </div>
    <div>			
      <p>
        Will anyone in your group require special accommodations?
      </p>
      <input 
        type="radio" 
        id="special_accommodations_toggle_on" 
        name="special_accommodations_toggle"
        :value="true" 
        v-model="needSpecial"
        @change="complete[2] = false">
      <label for="special_accommodations_toggle_on">Yes</label>
      &emsp;
      <input 
        type="radio" 
        id="special_accommodations_toggle_off" 
        name="special_accommodations_toggle"
        :value="false" 
        v-model="needSpecial"
        @change="complete[2] = true">
      <label for="special_accommodations_toggle_off">No</label>
    </div>
    <div id="special_accommodations_wrap" v-if="needSpecial">
      <label for="special_accomodations_text">
        Please explain below:
      </label>
      <textarea rows="10" cols="10" id="special_accomodations_text" v-model="special"></textarea>
    </div>
    <div class="step2__completed" v-if="complete[1] && complete[2]">OK</div>
  </fieldset>
</template>

<script>
export default {
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
