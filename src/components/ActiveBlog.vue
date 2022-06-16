<template>
  <div class="container-fluid">
    <div class="row">
      <div
        class="col-12 d-flex justify-content-center"
      >
        <img class="img-fluid" :src="activeBlog.imgUrl" alt="" />
      </div>
    </div>
  </div>
</template>


<script>
import { computed } from "@vue/reactivity";
import { AppState } from "../AppState";
export default {
  setup() {
    return {
      activeBlog: computed(() => AppState.activeBlog),
    };
  },
};
</script>


<style lang="scss" scoped>
</style>