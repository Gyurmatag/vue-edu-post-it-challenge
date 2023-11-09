<script setup lang="ts">
import { onMounted, ref } from "vue";
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
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

function reload() {
  loadPosts();
}
</script>

<template>
  <div
    class="min-h-screen py-6 flex flex-col items-center justify-center sm:py-12"
  >
    <h1 class="font-bold text-3xl">Post It!</h1>
    <section class="w-full max-w-2xl p-4 mb-6">
      <PostForm @reload="reload" />
    </section>
    <section class="w-full max-w-2xl p-4 bg-white">
      <PostList v-bind:posts="posts" />
    </section>
  </div>
</template>
