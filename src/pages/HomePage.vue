<template>
  <div class="container-fluid">
    <div class="row p-5 justify-content-between">
      <Blog v-for="b in blogs" :key="b.id" :blog="b" />
    </div>
  </div>
</template>

<script>
import { computed, onMounted } from "@vue/runtime-core";
import { logger } from "../utils/Logger";
import Pop from "../utils/Pop";
import { AppState } from "../AppState";
import { blogsService } from "../services/BlogsService";
export default {
  name: "Home",
  setup() {
    onMounted(async () => {
      try {
        AppState.blogs = [];
        await blogsService.getBlogs();
      } catch (error) {
        logger.error(error);
        Pop.toast(error.message, "error");
      }
    });
    return {
      blogs: computed(() => AppState.blogs),
    };
  },
};
</script>

<style scoped lang="scss">
.home {
  display: grid;
  height: 80vh;
  place-content: center;
  text-align: center;
  user-select: none;
  .home-card {
    width: 50vw;
    > img {
      height: 200px;
      max-width: 200px;
      width: 100%;
      object-fit: contain;
      object-position: center;
    }
  }
}
</style>
