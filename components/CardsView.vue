<!-- Please remove this file from your project -->
<template>
  <div class="relative flex items-top justify-center bg-gray-100">
    <div class="container">
      <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
        <p class="relative flex items-top justify-center text-8xl">Topigo</p>
        <Card :posts="allPosts" />
      </div>
    </div>
  </div>
</template>

<script>
import { mapMutations } from "vuex";

export default {
  name: "NuxtTutorial",
  computed: {
    allPosts() {
      return this.$store.state.posts.posts;
    },
  },
  methods: {
    addTodo(e) {
      this.$store.commit("posts/add", e.target.value);
      e.target.value = "";
    },
    ...mapMutations({
      toggle: "posts/toggle",
    }),
  },
};
</script>
