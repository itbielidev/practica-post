<script setup lang="ts">
import Formulari from './components/Formulari.vue';
import TextIcon from '@/components/icons/TextIcon.vue'
</script>

<template>
  <!-- <div class="principal">
  </div> -->
  
    <h1> <TextIcon /> My Journal</h1>



<section>
<Formulari>
</Formulari>
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
}

*{
  font-family: Arial, Helvetica, sans-serif;
  justify-content: center;
}

</style>