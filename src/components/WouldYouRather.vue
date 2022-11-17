<template>
  <div class="wyr">

    <h2>Would You Rather...</h2>

    <h3>{{ question }}</h3>

   <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
   <label>{{ answer1}}</label>

    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2}}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    // The types of each input to expect from the parent app are listed here
    id: Number,
    question: String,
    answer1: String,
    answer2: String,
    choices: []
  },
  data() {
    return {
      choice: ''
    }
  },
  methods: {
    //This transmits the users choice to the parent, app.vue and push the user's choice made for each question
    choiceMade() {
      this.$emit('answer-changed', this.id, this.choice)
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 25px;
}

.wyr {
  border: 2px solid darkolivegreen;
  background-color: burlywood;
  margin: 10px;
}
</style>

