<script setup lang="ts">
import { ref } from 'vue';
import { IPost } from '../interfaces/IPost.interface';

const emit = defineEmits<{
  formSubmit: [post: IPost]
}>()

let name = ref('')
let text = ref('')

const onFormSubmit = () => {
  if(name.value && text.value) {
    emit('formSubmit', { name: name.value, text: text.value})
  }
}
</script>

<template>
  <div class="rounded-lg p-6 bg-white shadow-md rounded-lg">
    <form @submit.prevent="onFormSubmit">
      <div class="mb-4">
        <label for="username" class="block text-gray-700 text-sm font-bold mb-2">Username</label>
        <input
          v-model="name"
          id="username"
          rows="4"
          type="text"
          placeholder="Your username"
          class="resize-y w-full px-3 py-2 text-gray-700 border rounded-lg focus:outline-none focus:shadow-outline"
        />
      </div>
      <div class="mb-4">
        <label
          for="postInput"
          class="block text-gray-700 text-sm font-bold mb-2">Your post</label>
        <textarea
          v-model="text"
          id="postInput"
          rows="4"
          placeholder="What's on your mind?"
          class="resize-y w-full px-3 py-2 text-gray-700 border rounded-lg focus:outline-none focus:shadow-outline"
        ></textarea>
      </div>
      <div class="flex justify-end">
        <button
          type="submit"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
        >
          Post
        </button>
      </div>
    </form>
  </div>
</template>
