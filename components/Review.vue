<template>
  <div>
    <div v-for="(review, idx) of postReview.review" :key="idx">
      <div v-if="review.content" class="py-2 mb-2">
        <div
          class="flex flex-col min-h-10 overflow-hidden ring-2 ring-green-400 shadow sm:rounded-lg bg-slate-50 mb-2 pl-2"
        >
          <div class="font-semibold">Отзыв:</div>
          <div>
            {{ review.content }}
          </div>
        </div>
        <div v-for="(item, idx) of review.comment" :key="idx">
          <div
            class="ring-2 ring-violet-400 sm:rounded-lg bg-slate-50 mb-2 pl-2"
          >
            <div class="font-semibold">Комментарий:</div>
            {{ item }}
          </div>
        </div>
        <div class="flex">
          <input
            class="w-3/4 rounded-lg ring-2 ring-violet-500"
            type="text"
            v-model="newComment[idx]"
            @keyup.enter="setNewComment(postReview.id, idx)"
          />
          <button
            class="rounded-lg ring-2 ring-violet-500 hover:bg-violet-200 ml-auto px-2 h-7"
            @click="setNewComment(postReview.id, idx)"
          >
            Написать комментарий
          </button>
        </div>
      </div>
    </div>

    <div class="flex justify-items-end h-10 my-8">
      <input
        class="w-3/4 rounded-lg ring-2 ring-green-500"
        type="text"
        v-model="newReview[postReview.id]"
        @keyup.enter="setNewReview(postReview.id)"

      />
      <button
        class="rounded-lg ring-2 ring-green-500 hover:bg-green-300 ml-auto px-2"
        @click="setNewReview(postReview.id)"
      >
        Оставить отзыв
      </button>
    </div>
  </div>
</template>
  
  <script>
export default {
  props: ["postReview"],
  data() {
    return {
      newReview: [],
      newComment: [],
    };
  },

  methods: {
    setNewReview(id) {
      let newReview = this.newReview[id];
      this.$store.commit("posts/addNewReview", { id, newReview });
      this.newReview[id] = "";
    },
    setNewComment(post_id, comment_id) {
      let comment = this.newComment[comment_id];
      this.$store.commit("posts/addNewComment", {
        post_id,
        comment_id,
        comment,
      });
      this.newComment[comment_id] = "";
    },
  },
};
</script>
  
  <style>
</style>