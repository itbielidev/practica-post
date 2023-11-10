<template>
    <!-- <h2>Formulari</h2> -->
    <form  @submit.prevent="gestionarSubmit">
    <textarea :value="body" 
    @keyup="recollirTextForm"
    ref="textarea" class="text-box" name="" id="" cols="60" rows="10" placeholder="Escribe un post">
    </textarea>
    <Emojis v-model="emoji"></Emojis>
    <span>{{ charCount }} / {{ maxCharacters }}</span>
    <button class="submitButton" type="submit">Remember <SubmitButton/></button>
  </form>
</template>

<script setup lang="ts">
import type Entry from '@/types/Entry';
import { computed, ref } from 'vue';
import Emojis from '../components/icons/Emojis.vue';
import SubmitButton from './icons/SubmitButton.vue';
import type Emoji from '@/types/Emojis.ts';


//explicar
const emit = defineEmits<{
  (e:"@create",entry:Entry):void
}>(); 

const maxCharacters = 280;
//fer referencia al num de caracters del formulari 
const body =ref("")
const emoji = ref<Emoji| null>(null)
const charCount = computed(()=>body.value.length)
console.log(charCount)
const recollirTextForm = (e:Event) =>{
  const textarea = e.target as HTMLTextAreaElement
  
  if (textarea.value.length<=maxCharacters) {
    body.value = textarea.value   
  } else{
   /* <div v-if="">
    Se ha superado el limite de caracteres
    </div> */
  }
 
}

const gestionarSubmit = ()=>{
  console.log("hola")
  emit('@create', {
    id: 1,
    emoji: emoji.value,
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
  width: 50rem;
  margin:auto;
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