<template>
  <div id="app">

    <h1>Would You Rather?</h1>

    <would-you-rather
       v-for="question in questions"
       v-bind:id="question.id"
       v-bind:question="question.question"
       v-bind:answer1="question.answer1"
       v-bind:answer2="question.answer2"
       v-on:answer-changed="answerChanged"></would-you-rather>

    <h2>Your answer</h2>

    <p v-for="choice in choices">{{ choice }}</p>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      choices: [],
      //An array of questions and answers used for the app
      questions: [
        {
          id: 0,
          question: '...be an incredibly fast swimmer or an incredibly fast runner?',
          answer1: 'Fast swimmer',
          answer2: 'Fast runner',
          },
        {
          id: 1,
          question: '...be really good at math or really good at sports?',
          answer1: 'Good at math',
          answer2: 'Good at sports',
          },
        {
          id: 2,
          question: '...have the ability to see 10 minutes into the future or 10 years into the future?',
          answer1: '10 minutes',
          answer2: '10 years',
        },
      ],
      userSelectionMessage:'' // Set to empty, expecting user input
    }
  },
  methods: { //
    answerChanged(id, choice) {
      this.choices[id] = choice
    }
  }
}
</script>

<style>

body {
  background: darkgray;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>