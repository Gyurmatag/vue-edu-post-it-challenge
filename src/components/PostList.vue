<script setup lang="ts">
import Post from "./Post.vue";
import { IPost } from '../interfaces/IPost.interface'

defineProps<{posts: IPost[]}>()
</script>

<template>
  <div class="flex flex-col space-y-4">
    <Post v-for="item in posts" :key="item" :name="item.name" :text="item.text" />
  </div>
</template>
