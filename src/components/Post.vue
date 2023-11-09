<script setup lang="ts">
defineProps(["post"]);
</script>

<template>
  <div class="p-4 bg-white shadow-md rounded-lg">
    <header class="flex items-center justify-between mb-2">
      <span class="font-bold text-lg">{{ post.users.name }}</span>
    </header>
    <p>{{ post.posts.text }}</p>
  </div>
</template>
