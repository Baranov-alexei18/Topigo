<template>
  <div>
    <div v-for="(item, idx) of posts" :key="idx">
      <div
        class="flex bg-white min-h-40 overflow-hidden shadow sm:rounded-lg bg-slate-50 mb-2"
        @click="toPost(item.id)"
      >
        <div class="flex justify-between">
          <div class="m-2 w-full text-wrap mr-auto">
            <p class="font-semibold">Title: {{ item.title }}</p>
            <p class="font-semibold">Description: {{ item.desc }}</p>
          </div>

          <div class="flex w-60">
            <img class="min-h-40 h-44" :src="item.img" />
          </div>
        </div>
      </div>
      <div v-for="(review, idx) of item.review" :key="idx">
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
              v-model="newComment[item.id]"
            />
            <button
              class="rounded-lg ring-2 ring-violet-500 hover:bg-violet-200 ml-auto px-2 h-7"
              @click="setNewComment(item.id)"
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
          v-model="newReview[item.id]"
        />
        <button
          class="rounded-lg ring-2 ring-green-500 hover:bg-green-300 ml-auto px-2"
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
      newReview: [],
      newComment: [],
    };
  },

  methods: {
    toPost(id) {
      console.log(id);
      this.$router.push({ path: `/post/${id}`, params: {id: "sdf"} });
    },

    setNewReview(id) {
      let newReview = this.newReview[id];
      this.$store.commit("posts/addNewReview", { id, newReview });
      this.newReview[id] = "";
    },
    setNewComment(id) {
      console.log(this.newComment[id]);
      let comment = this.newComment[id];
      this.$store.commit("posts/addNewComment", { id, comment });
      this.newComment[id] = "";
    },
  },
};
</script>

<style>
</style>