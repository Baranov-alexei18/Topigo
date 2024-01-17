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
      <Review :post-review="item"/>

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
      this.$router.push({ path: `/post/${id}`});
    },

    setNewReview(id) {
      let newReview = this.newReview[id];
      this.$store.commit("posts/addNewReview", { id, newReview });
      this.newReview[id] = "";
    },
    setNewComment(post_id, comment_id) {
      let comment = this.newComment[post_id];
      this.$store.commit("posts/addNewComment", { post_id, comment_id, comment });
      this.newComment[post_id] = "";
    },
  },
};
</script>

<style>
</style>