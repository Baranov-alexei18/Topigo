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
        <div
          v-if="item.content"
          class="flex bg-slate-100 h-20 overflow-hidden shadow sm:rounded-lg bg-slate-50 mb-2"
        >
          {{ item.content }}
        </div>
      </div>
      
      <div class="flex justify-items-end h-10 mb-5">
        <input class="rounded-lg ring-2 ring-blue-500" type="text" v-model="newComment" />
        <button class="rounded-lg ring-2 ring-blue-500 ml-auto" @click="checkWriteComment = true">
          Написать комментарий
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
        newComment: "",
    }
  },

  methods: {
    toPost() {
      this.$router.push("/post");
    },
  },
};
</script>

<style>
</style>