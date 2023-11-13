<script setup lang="ts">
  import { IPost } from '../interfaces/IPost.interface';

  defineProps<IPost>()
</script>

<template>
  <div class="p-4 bg-white shadow-md rounded-lg">
    <header class="flex items-center justify-between mb-2">
      <span class="font-bold text-lg">{{ name }}</span>
    </header>
    <p>{{ text }}</p>
  </div>
</template>
