<script setup>

import {defineProps, defineEmits} from "vue"

    const emit = defineEmits(["selectOption"])
    const {question} =defineProps(['question'])
    const emitSelectedOption = (isCorrect) =>{
        emit("selectOption", isCorrect)
    }
</script>
<template> 
    <div class="question-container">
        <h1 class="questions">
            {{ question.text }}
        </h1>
     </div>

    <div class="options-container">
        <div v-for="option in question.options"
         :key="option.id"  
         class="option" 
         @click="emitSelectedOption(option.isCorrect)"
         >
            <p class="option-lebel">{{ option.label }}</p>
            <div class="option-value">
                <p>{{ option.text }}</p>
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
    .option-lebel{
        background-color: bisque;
        width: 50px;
        height: 50px;
        font-size: 30px;
        display: flex;
        align-items: c enter;
        justify-content: center;
    }

    .option-value{
        background-color: rgb(244, 239, 239);
        width: 90%;
        font-size: 30px ;
        padding: 0 20px;

    }

</style>