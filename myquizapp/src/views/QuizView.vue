
<script setup>
import {useRoute} from "vue-router"
import { ref, computed } from "vue";
import Question from "../components/Question.vue"
import QuizHeader from "../components/QuizHeader.vue"
import quizes from "../data/quizes.json"
const route = useRoute();
const quizId =  parseInt(route.params.id);
const quiz= quizes.find(q =>q.id === quizId)
const currentQuestionIndex = ref(0);
const onOptionSelected =(isCorrect)=>{
    console.log("*********onOptionSelected******");
    if (isCorrect){
        
    }
    if (currentQuestionIndex.value <= quiz.questions.length-1 ){
        currentQuestionIndex.value +=1;
    }
}
const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const barPercentage = computed(() => `${currentQuestionIndex.value/quiz.questions.length * 100}%`)
</script>
<template>
    <QuizHeader 
            :questionStatus="questionStatus"
            :barPercentage="barPercentage"
        />

    <div>
        <Question :question="quiz.questions[currentQuestionIndex]" @selectOption="onOptionSelected" />
    </div>
</template>