<template>
  <div>
    <ol>
      <li v-for="answer in answers">
        {{answer}}
      </li>
    </ol>
<!--
      <li answer.forEach("(answer, question) in answers, questions">
        (num1, index) => {const num2 = questions[index];
  console.log(num1, num2);})>
  ) v-for="answer in answers" :item="answer" :key="index">-->
      
    </li>
    </div>
</template>

<script>
export default {
  Name: "Summary",
  props: ['answers'], 
  
  
}
</script>

