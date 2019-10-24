<template>
  <div>
    <ol>
      <li v-for="answer in answers">{{answer}}</li>
    </ol>
  </div>
</template>

<script>
export default {
  Name: "Summary",
  props: ["answers"]
};
</script>

