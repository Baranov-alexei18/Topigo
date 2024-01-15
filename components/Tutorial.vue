<!-- Please remove this file from your project -->
<template>
  <div
    class="relative flex items-top justify-center bg-gray-100 sm:items-center sm:pt-0"
  >
    <link
      href="https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css"
      rel="stylesheet"
    />
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <p class="relative flex items-top justify-center text-8xl">Topigo</p>
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-2xl leading-7 font-semibold">
          Welcome to your Nuxt Application
        </h2>
        <p class="mt-3 text-gray-600">
          We recommend you take a look at the
          <a
            href="https://nuxtjs.org"
            target="_blank"
            class="button--doc text-green-500 hover:underline"
            >Nuxt Documentation</a
          >, whether you are new or have previous experience with the
          framework.<br />
        </p>
        <p class="mt-4 pt-4 text-gray-800 border-t border-dashed">
          To get started, remove
          <code class="bg-gray-100 text-sm p-1 rounded border"
            >components/Tutorial.vue</code
          >
          and start coding in
          <code class="bg-gray-100 text-sm p-1 rounded border"
            >pages/index.vue</code
          >. Have fun!
        </p>
      </div>
      <ul>
        <li v-for="todo in todos" :key="todo.text">
          <input :checked="todo.done" @change="toggle(todo)" type="checkbox" />
          <span :class="{ done: todo.done }">{{ todo.text }}</span>
        </li>
        <li>
          <input @keyup.enter="addTodo" placeholder="What needs to be done?" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { mapMutations } from "vuex";

export default {
  name: "NuxtTutorial",
  computed: {
    todos() {
      return this.$store.state.posts.list;
    },
  },
  methods: {
    addTodo(e) {
      this.$store.commit('posts/add',e.target.value);
      e.target.value = "";
    },
    ...mapMutations({
      toggle: "posts/toggle",
    }),
  },
};
</script>
