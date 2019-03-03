<template>
  <fieldset id="step_1">
    <legend>Step 1</legend>
    <label for="num_attendees">
      How many people will be attending?
    </label>
    <select id="num_attendees" v-model="attNo">
      <option id="opt_0" value="0">Please Choose</option>
      <option :id="'opt_'+a" :value="a" v-for="a in maxAtt" :key="a">{{ a }}</option>
    </select>
    <br>
    <div id="attendee_container" v-if="attNo !== 0">
      <h3>Please provide full names:</h3>
      <div id="attendee_wrap" v-for="a in attNo" :key="a">
        <label :for="'name_attendee_'+a">
          Attendee {{ a }} Name:
        </label>
        <input type="text" :id="'name_attendee_'+a" v-model="attList[a-1]">
      </div>
      <div id="step1_result"></div>
    </div>
    <div class="step1__completed" v-if="complete">OK</div>
  </fieldset> 
</template>

<script>
export default {
  data() {
    return {
      maxAtt: 5,
      attNo: 0,
      attList: [],
      complete: false
    }
  },
  watch: {
    attList() {
      if (this.attList.length === this.attNo && this.attList.length > 0 && this.attList.every(a => {return a !== ""})) {
        this.complete = true
        this.$emit("complete1", true)
      } else {
        this.complete = false
        this.$emit("complete1", false)
      }
    },
    attNo() {
      if (this.attList.length !== this.attNo && this.attList.length > 0) {
        this.complete = true
        this.$emit("complete1", true)
      }
    }
  }
}
</script>
