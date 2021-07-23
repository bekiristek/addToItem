<template>
  <div class="progress">
    <div
      class="progress-bar bg-info"
      role="progressbar"
      :style="{ width: progressBar + '%' }"
      aria-valuenow="50"
      aria-valuemin="0"
      aria-valuemax="100"
    >
      {{ currentItem }}/10
    </div>
  </div>
</template>

<script>
import { eventBus } from "../main";
export default {
  data() {
    return {
      currentItem: 0,
      progressBar: 0,
    };
  },

  created() {
    eventBus.$on("progressBarUpdated", (productListCount) => {
      this.currentItem = productListCount;
      this.progressBar = productListCount * 10;
    });
  },
};
</script>