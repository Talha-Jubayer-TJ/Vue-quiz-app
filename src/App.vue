<script setup>
  import {RouterView} from "vue-router"
  import QuizesView from "./Views/QuizesView.vue"
</script>


<template>
    <div class="container">
      <!-- <QuizesView /> -->
            <RouterView />

    </div>
</template>

<style scoped>

.container{
    max-width: 1000px;
    margin: 0 auto;
  }
</style>