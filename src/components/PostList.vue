<template>
  <div class="post-list">
    <article v-for="post in posts" :key="post._id" class="card mb-3 shadow-sm">
      <div class="card-body">
        <h4>{{post.title}}</h4>
        <div class="row my-3 align-items-center">
          <div v-if="post.image" class="col-4">
            <img :src="post.image.fitUrl" :alt="post.title" class="rounded-lg w-100" />
          </div>
          <p :class="{'col-8': post.image}" class="text-muted">{{post.excerpt}}</p>
        </div>
        <span class="text-muted">{{post.createdAt}}</span>
      </div>
    </article>
  </div>
</template>

<script lang='ts'>
import { defineComponent, PropType } from "vue";
import { PostProps } from "../testData";
export default defineComponent({
  props: {
    list: {
      type: Array as PropType<PostProps[]>,
      required: true,
    },
  },
  setup(props) {
    return {
      posts:props.list
    };
  },
});
</script>

<style>
</style>