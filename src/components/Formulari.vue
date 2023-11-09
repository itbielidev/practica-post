<template>
    <!-- <h2>Formulari</h2> -->
    <form  @submit="gestionarSubmit" action="">
    <textarea :value="body" ref="textarea" class="text-box" name="" id="" cols="60" rows="10" placeholder="Escribe un post">

    </textarea>
    <Emojis></Emojis>
    <button class="submitButton" type="submit">Remember <SubmitButton/></button>
  </form>
</template>

<script setup lang="ts">
import type Entry from '@/types/Entry';
import { computed, ref } from 'vue';
import Emojis from '../components/icons/Emojis.vue';
import SubmitButton from './icons/SubmitButton.vue';

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
  background-color:#e4e4eb;
  gap:10px;
  padding: 15px;
  display: flex;
  flex-direction: column;
  border-radius: 5px;
}

.text-box{
  border: white;
  font-size: 15px;
  font-family: Arial, Helvetica, sans-serif;
}

.submitButton{
  align-self: flex-end;
  background-color:#237171 ;
  border: 0px;
  font-size: 15px;
  color: white;
  padding: 5px;
  border-radius: 5px;
  font-weight:lighter;
  align-items: center;
}

</style>