<script setup>
const currentUser = ref({
  username: 'user',
})

const posts = ref([])

const newPostContent = ref('')

const addPost = () => {
  posts.value.push({ content: newPostContent.value })
  newPostContent.value = ''
}
</script>

<template>
  <div class="h-screen w-full bg-gray-200 flex items-center justify-center">
    <div class="max-w-sm w-full">
      <div class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
        <div class="mb-4">
          <h1 class="text-center text-2xl font-bold">
            {{ currentUser.usernae }}'s posts:
          </h1>
        </div>
        <div class="mb-4">
          <ul class="text-gray-700 text-base list-none">
            <li v-for="(post, idx) in posts" :key="idx">
              {{ post.content }}
            </li>
          </ul>
        </div>
        <div class="mb-4">
          <form @submit.prevent.stop="() => ({})">
            <div class="flex flex-col justify-center space-y-4">
              <input
                v-model="newPostContent"
                placeholder="Type some text..."
                class="border-2 transition-colors duration-300 border-solid hover:border-blue-300 border-gray-200 rounded-10px px-4 w-full leading-2rem outline-none !focus:border-blue-500"
              >
              <button
                class="block bg-blue-500 text-white font-semibold leading-3rem rounded w-full px-4"
                @click="addPost"
              >
                Add Post
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
