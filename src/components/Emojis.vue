<template>
   <div class="emoji-box">
     <!-- happy face -->
     <button type="button" @click="() => select('happy')" class="btn-icon hover">
        <EmojiIcon icon="happy" /> 
     </button>
     <button type="button" @click="() => select('sad')" class="btn-icon hover">
        <EmojiIcon icon="sad" /> 
     </button>
     <button type="button" @click="() => select('surprised')" class="btn-icon hover">
        <EmojiIcon icon="surprised" /> 
     </button>
   </div>
</template>



<script setup lang="ts">
import type Emoji from '@/types/Emojis';
import EmojiIcon from './icons/EmojiIcon.vue';

const emit = defineEmits<{
  (e:"selectEmoji", emoji: Emoji):void
}>(); 

const select = (emoji: Emoji) => {
  emit('selectEmoji', emoji)
} 
</script>

<style>
.emoji-box{
    margin-top:10px ;
    display: flex;
    flex-direction: row;
    gap: 5px;
    
}
.btn-icon {
  font-size: 30px;
  background: none;
  border: none;
}

.btn-icon:hover{
  color: #237171;
}
</style>