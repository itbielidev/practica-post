<script setup lang="ts">
import Formulari from './components/Formulari.vue';
import TextIcon from '@/components/icons/TextIcon.vue'
import PostEnviat from '@/components/PostEnviat.vue'
</script>

<template>

    <h1> <TextIcon /> My Journal</h1>

<section>
<Formulari/>
<PostEnviat/>
</section>
</template>

<style scoped>
/* .principal{
  width: 100%;

} */



h1{
  font-weight: bold;
  text-align: center;
  
}

section{
  display: flex;
  flex-direction: column;
}

*{
  font-family: Arial, Helvetica, sans-serif;
  justify-content: center;
}

</style>