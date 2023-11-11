<script setup lang="ts">
import type Entry from '@/types/Entry';
import EmojiIcon from './icons/EmojiIcon.vue';

const props = defineProps<{
  entry: Entry
}>()

const relativeTime =  Math.ceil((props.entry.createDate.getTime() - new Date().getTime()) / (1000 * 60 * 60 * 24))

</script>

<template>

<div class="container-post">
  <div class="post-header">
    <span class="icon"><EmojiIcon v-if="props.entry.emoji" :icon="props.entry.emoji" /></span>
    <p>{{ props.entry.body }}</p>
  </div>
  <div class="post-footer">
    <span>{{ new Intl.RelativeTimeFormat('es', {numeric: "auto"}).format(relativeTime, "day") }}</span> | <span class="user">{{ props.entry.user }}</span>
  </div>
</div>
</template>

<style scoped>
.container-post{
  margin: 20px auto; 
  background-color: #e4e4eb;
  width: 50rem;
  border-radius: 5px;
  padding: 15px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.post-header {
  display: flex;
  align-items: center;
  gap: 10px;
}
.post-header .icon {
  font-size: 4rem;
  display: flex;
}
.post-footer {
  display: flex;
  align-self: flex-end;
  gap: 10px;
  align-items: center;
}
.post-footer .user {
  color: #237171;
}
</style>