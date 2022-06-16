<template>
  <div class="col-4 rounded elevation-3 selectable" @click="setActive">
    <h1>{{ blog.title }}</h1>
    <p>{{ blog.body }}</p>
    <img class="img-fluid" :src="blog.imgUrl" alt="" />
  </div>
</template>


<script>
import { computed } from "@vue/reactivity";
import { blogsService } from "../services/BlogsService";
import { AppState } from "../AppState";
import { Modal } from "bootstrap";
export default {
  props: { blog: { type: Object, required: true } },
  setup(props) {
    return {
      setActive() {
        blogsService.setActive(props.blog);
        Modal.getOrCreateInstance(document.getElementById("blog-modal")).show();
      },
    };
  },
};
</script>


<style lang="scss" scoped>
</style>