<script setup lang="ts">
import { onMounted, ref } from "vue";
import Post from "./Post.vue";

import axios from "axios";

interface Post {
  posts: {
    id: number;
    text: string;
    createdAt: string;
    userId: number;
  };
  users: {
    id: number;
    name: string;
  };
}
const posts = ref<Post[]>([]);

function loadPosts() {
  axios
    .get<Post[]>("https://edge-post.vercel.app/api/posts")
    .then((response) => {
      posts.value = response.data;
    });
}

onMounted(() => {
  loadPosts();
});
</script>

<template>
  <div class="flex flex-col space-y-4">
    <Post v-for="post in posts" v-bind:post="post" />
  </div>
</template>
