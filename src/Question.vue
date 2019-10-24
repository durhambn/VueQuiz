<template>
  <div
    id="question"
    v-bind:style="{ 'display': changeDisplay}"
    v-show="numOfAnswers === question.id"
  >
    <h1>Question {{question.id}}</h1>
    <h3>{{question.text}}</h3>
    <div
      id="answers"
      v-bind:style="{'display': changeDisplay}"
      v-for="answer in question.answers"
      v-bind:key="answer[index]"
    >
      <input type="radio" name="answer" v-model="quizAnswer" v-bind:value="answer">
      <label>{{answer}}</label>
    </div>
    <button v-show="quizAnswer" v-on:click="setAnswer">Submit</button>
  </div>
</template>

<script>
export default {
  Name: "Question",
  props: ["question", "numOfAnswers"],
  data() {
    return {
      quizAnswer: "",
      showQuestion: true,
      display: "block"
    };
  },
  computed: {
    changeDisplay: function() {
      return this.display;
    }
  },
  methods: {
    setAnswer: function() {
      //console.log(this.quizAnswer);
      this.$emit("userAnswer", this.quizAnswer);
      this.showQuestions = false;
      this.display = "none";

      
    }
  }
};
</script>


