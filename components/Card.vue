<template>
  <div>
    <div v-for="(item, idx) in posts" :key="idx">
      <div
        class="flex bg-white min-h-40 overflow-hidden shadow sm:rounded-lg bg-slate-50 mb-2"
        @click="toPost"
      >
        <div class="flex justify-between">
          <div class="m-2 w-full text-wrap mr-auto">
            <p>
              <b>Title: {{ item.title }}</b>
            </p>
            <p>
              <b>Description: {{ item.desc }}</b>
            </p>
          </div>

          <div class="flex w-60">
            <img class="min-h-40 h-44" :src="item.img" />
          </div>
        </div>
      </div>
      <div v-for="item in item.comment" :key="item">
        <div v-if="item.content" class="py-2 mb-2">
          <div
            class="flex bg-slate-100 min-h-10 overflow-hidden shadow sm:rounded-lg bg-slate-50 mb-2 pl-2"
          >
            {{ item.content }}
          </div>
          <div class="flex">
            <button
              class="rounded-lg ring-2 ring-green-400 ml-auto px-2 h-7"
              @click="addNewComment(item.id)"
            >
              Написать комментарий
            </button>
          </div>
        </div>
      </div>

      <div class="flex justify-items-end h-10 my-8">
        <input
          class="w-3/4 rounded-lg ring-2 ring-blue-500"
          type="text"
          v-model="newComment[item.id]"
        />
        <button
          class="rounded-lg ring-2 ring-blue-500 ml-auto px-2"
          @click="setNewReview(item.id)"
        >
          Оставить отзыв
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["posts"],
  data() {
    return {
      checkWriteComment: false,
      newComment: [],
      newReview: [],
    };
  },

  methods: {
    toPost() {
      this.$router.push("/post");
    },

    setNewReview(id) {
      let newComment = this.newComment[id];
      this.$store.commit("posts/setNewReview", { id, newComment });
      this.newComment[id] = "";
    },
    addNewComment(id) {
      this.$store.commit("posts/addNewComment", { id, newComment });
    },
  },
};
</script>

<style>
</style>