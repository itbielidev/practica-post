<template>
    <form  @submit.prevent="gestionarSubmit">
    <textarea v-model="body"
    ref="textarea" class="text-box" maxlength="280" name="" id="" cols="60" rows="10" placeholder="Escribe un post">
    </textarea>
    <Emojis @select-emoji="(emoji) => selectEmoji(emoji)"></Emojis>
    <span>{{ charCount }} / {{ maxCharacters }}</span>
    <button class="submitButton" type="submit">Remember <SubmitButton/></button>
  </form>
</template>

<script setup lang="ts">
import type Entry from '@/types/Entry';
import { computed, ref } from 'vue';
import Emojis from '@/components/Emojis.vue';
import SubmitButton from './icons/SubmitButton.vue';
import type Emoji from '@/types/Emojis.ts';

//explicar
const emit = defineEmits<{
  (e:"create",entry:Entry):void
}>(); 

const maxCharacters = 280;
//fer referencia al num de caracters del formulari 
const body =ref("")
const emoji = ref<Emoji| null>(null)
const charCount = computed(()=>body.value.length)

const selectEmoji = (selectedEmoji: Emoji) => {
  emoji.value = selectedEmoji
}

const gestionarSubmit = ()=>{
  
  emit('create', {
    id: 1,
    emoji: emoji.value,
    createDate: new Date("2023-11-11 08:30:00"),
    user: 'carolina',
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