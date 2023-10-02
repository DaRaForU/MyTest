<script setup>
  import {defineProps} from 'vue';

  const {question} = defineProps(['question']);



</script>

<template>

  <div class="question-container">
    <h1 class="question">
      {{ question.text }}
    </h1>
  </div>

  <div class="options-container">

    <div v-for="option in question.options" class="option">
      <p class="option-label">{{ option.label }}</p>
      <div class="option-value">
        <p>{{option.text}}</p>
      </div>
    </div>

  </div>
</template>

<style scoped>
  .question-container{
    margin-top: 20px;
  }
  .question{
    font-size: 40px;
    margin-bottom: 20px;
  }
  .option{
    display: flex;
    margin-bottom: 20px;
    cursor: pointer;
  }
  .option-label{
    background-color: bisque;
    width: 60px;
    height: 60px;
    font-size: 30px;
    color: black;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .option-value{
    background-color: rgb(244, 239, 239);
    font-size: 30px;
    width: 100%;
    padding: 0 20px;
    display: flex;
    align-items: center;
  }
  .option-value p{
    color: black;
  }

</style>