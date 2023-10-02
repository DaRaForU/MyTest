<script setup>
  import {useRoute, useRouter} from 'vue-router';
  import {ref, watch, computed} from 'vue';
  import Question from '../components/Question.vue';
  import QuizHeader from '../components/QuizHeader.vue';
  import quizes from '../data/quizes.json';

  const route = useRoute();
  const quizId = parseInt(route.params.id);

  const quiz = quizes.find(q => q.id === quizId);

  const currentQuestionIndex = ref(0);

  const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`);

  watch(() => currentQuestionIndex.value, () => {
    questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`;
  });

  // const questionStatus = computed(() => {
  //   return `${currentQuestionIndex.value}/${quiz.questions.length}`;  
  // });

  const barPercentage = computed(() => {
    return `${(currentQuestionIndex.value/quiz.questions.length)*100}%`
  });


</script>

<template>
  <div>
    
    <QuizHeader :questionStatus="questionStatus" :barPercentage="barPercentage" />

    <div>
      <Question :question="quiz.questions[currentQuestionIndex]" />
    </div>
  </div>

  <button @click="currentQuestionIndex++">Next Question</button>

</template>

<style scoped>
  a{
    color: red
  }
</style>