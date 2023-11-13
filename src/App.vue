<script setup lang="ts">
import { ref, onBeforeMount } from "vue";
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import { IPost } from "./interfaces/IPost.interface";
import axios from 'axios'

const postList = ref<IPost[]>([]) 

onBeforeMount(async () => {
  try {
    const response = await axios.get('/api/posts')

    postList.value = response.data.map((item) => ({
      name: item.users.name,
      text: item.posts.text
    }))
  } catch (error) {
    postList.value = []
  }
})

const onFormSubmit = async (event: IPost) => {
  const response = await axios.post('/api/posts', event)

  if(response.status === 200) {
    postList.value = [...postList.value, event]
  }
}
</script>

<template>
  <div
    class="min-h-screen py-6 flex flex-col items-center justify-center sm:py-12"
  >
    <h1 class="font-bold text-3xl">Post It!</h1>
    <section class="w-full max-w-2xl p-4 mb-6">
      <PostForm @formSubmit="onFormSubmit"/>
    </section>
    <section class="w-full max-w-2xl p-4 bg-white">
      <PostList :posts="postList.values()"/>
    </section>
  </div>
</template>
