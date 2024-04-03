<script setup>
import Question from "../components/Question.vue"
import QuizHeader from "../components/QuizHeader.vue"
import {useRoute} from 'vue-router'
import {ref, watch, computed} from "vue"
import quizes from "../data/quizes.json"
import Result from '../components/Result.vue'


const route= useRoute()
const quizId =parseInt(route.params.id)
const quiz = quizes.find(q => q.id === quizId)

const currentQuestionIndex = ref(0)

const numberOfCorrectAns = ref(0)

const showResult = ref(false)

const onOptionSelected = (isCorrect) =>{
  if(isCorrect){
    numberOfCorrectAns.value++;
  }
  
  if(quiz.questions.length -1 === currentQuestionIndex.value){
    showResult.value= true
  }

  currentQuestionIndex.value++;
}

// const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)

// watch(()=> currentQuestionIndex.value, ()=>{
//   questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`
// })

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)

const barParcent = computed(() => `${currentQuestionIndex.value/quiz.questions.length *100}%`)

</script>


<template>
    <div> 
        <QuizHeader 
          :questionStatus = "questionStatus"
          :barParcent="barParcent"
          />
      <div>
        <Question 

        v-if="!showResult"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
        /> 
        <Result v-else 
          :quizQuestionLength="quiz.questions.length"
          :numberOfCorrectAns="numberOfCorrectAns"
        />
      </div>
  </div>
</template>
