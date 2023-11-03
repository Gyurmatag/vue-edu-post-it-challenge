<script setup lang="ts">
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
</script>

<template>
  <div
    class="min-h-screen py-6 flex flex-col items-center justify-center sm:py-12"
  >
    <h1 class="font-bold text-3xl">Post It!</h1>
    <section class="w-full max-w-2xl p-4 mb-6">
      <PostForm />
    </section>
    <section class="w-full max-w-2xl p-4 bg-white">
      <PostList />
    </section>
  </div>
</template>
