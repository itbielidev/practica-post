<template>
    <!-- <h2>Formulari</h2> -->
    <form  @submit="gestionarSubmit" action="">
    <textarea :value="body" ref="textarea" name="" id="" cols="30" rows="10">

    </textarea>
    <Emojis></Emojis>
    <button class="submitButton" type="submit">Remember</button>
  </form>
</template>

<script setup lang="ts">
import type Entry from '@/types/Entry';
import { computed, ref } from 'vue';
import Emojis from '../components/icons/Emojis.vue';

const emit = defineEmits<{
  (e:"@create",entry:Entry):void
}>();

const textarea = ref()
const maxCharacters = 280;
//fer referencia al num de caracters del formulari 
const body =ref("")
const charCount = computed(()=>body.value)
console.log(charCount)
const recollirTextForm = (e:Event) =>{
console.log(textarea.value);

}

const gestionarSubmit = ()=>{
  console.log("hola")
  emit('@create', {
    id: 1,
    emoji: "happy",
    createDate: new Date(),
    userId: 1,
    body:body.value,
  })
}

</script>

<style scoped>
form{
  padding: 20px;
  background-color: lightgrey;
  gap:10px
}



</style>