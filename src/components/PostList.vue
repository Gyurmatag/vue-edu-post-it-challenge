<script setup lang="ts">
import Post from "./Post.vue";
defineProps(["posts"]);
</script>

<template>
  <div class="flex flex-col space-y-4">
    <Post v-for="post in posts" v-bind:post="post" />
  </div>
</template>
