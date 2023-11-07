<template>
    <h2>Formulari</h2>
    <form  @submit="gestionarSubmit" action="">
    <textarea :value="body" ref="textarea" name="" id="" cols="30" rows="10">

    </textarea>
    <Emojis></Emojis>
    <button type="submit">Remember</button>
  </form>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue/dist/vue.js';
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
    body:body.value,
  })
}

</script>