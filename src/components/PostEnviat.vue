<script setup lang="ts">
import type Entry from '@/types/Entry';
import EmojiIcon from './icons/EmojiIcon.vue';

const props = defineProps<{
  entry: Entry
}>()

</script>

<template>

<div class="container-post">
  <EmojiIcon v-if="props.entry.emoji" :icon="props.entry.emoji" />
  <div>
    {{ props.entry.body }}
  </div>
  {{ props.entry.createDate.toLocaleString() }}
  {{ props.entry.user }}
</div>
</template>

<style scoped>
.container-post{
  margin: 20px auto; 
  background-color: #e4e4eb;
  width: 50rem;
  border-radius: 5px;
  padding: 15px;
  
}
</style>