<script setup>

    import {defineProps} from "vue"

    const {
        questionStatus,
         barParcent
        } = 
        defineProps([
            "questionStatus" ,
            "barParcent"
        ])

    //console.log(questionStatus)
</script>

<template>
    <div>
    <header>
        
        <h4>Questions {{ questionStatus }} </h4>
        <div class="bar">
            <div class="completion" :style="{width:barParcent}">
            </div>                
        </div>
    </header>
    </div>
</template>


<style scoped>
    header {
        margin-top: 30px;
    }

    header h4{
        font-size: 30px;
    }

    .bar{
        width: 300px;
        height: 50px;
        border: 3px solid bisque;
    }
    .completion{
        height: 100%;
        width: 0%;
        background-color: bisque;
    }
</style>