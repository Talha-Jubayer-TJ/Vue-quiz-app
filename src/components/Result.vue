<script setup >
    import {defineProps} from 'vue'
    import {RouterLink} from "vue-router" 
    const {numberOfCorrectAns,quizQuestionLength } =defineProps(["quizQuestionLength","numberOfCorrectAns"])

</script>

<template>
    <div class="result">
        <p>Your Result</p>

        <h1>
            {{ numberOfCorrectAns }}/{{ quizQuestionLength }}
        </h1>
        <RouterLink to="/"> Go Back to HOME </RouterLink>
    </div>

</template>

<style scoped>
    .result{
        text-align: center;
        padding: 100px 0;
    }

    p{
        font-size: 25px;

    }
    h1{
        font-size: 80px;
    }
</style>