<template>
  <div class="rounded-lg p-6 bg-white shadow-md rounded-lg">
    <form @submit.prevent="onSubmit">
      <div class="mb-4">
        <label for="username" class="block text-gray-700 text-sm font-bold mb-2"
          >Username</label
        >
        <input
          id="username"
          rows="4"
          type="text"
          placeholder="Your username"
          class="resize-y w-full px-3 py-2 text-gray-700 border rounded-lg focus:outline-none focus:shadow-outline"
          v-model="username"
        />
      </div>
      <div class="mb-4">
        <label
          for="postInput"
          class="block text-gray-700 text-sm font-bold mb-2"
          >Your post</label
        >
        <textarea
          id="postInput"
          rows="4"
          placeholder="What's on your mind?"
          class="resize-y w-full px-3 py-2 text-gray-700 border rounded-lg focus:outline-none focus:shadow-outline"
          v-model="postInput"
        ></textarea>
      </div>
      <div class="flex justify-end">
        <button
          type="submit"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          :disabled="!username || !postInput"
        >
          Post
        </button>
      </div>
    </form>
  </div>
</template>
<script setup lang="ts">
import axios from "axios";
import { ref } from "vue";

const username = ref("");
const postInput = ref("");

const emit = defineEmits(["reload"]);

function onSubmit() {
  interface Data {
    name: string;
    text: string;
  }
  const data: Data = {
    name: username.value,
    text: postInput.value,
  };
  axios
    .post("https://edge-post.vercel.app/api/posts", data)
    .then((response) => {
      emit("reload");
    });
}
</script>
