<template>
  <div class="step">
    <!-- 執行到的時候下拉 -->
    <div class="header">
      <div>{{ title }}</div>
      <div>{{ isFinished }}</div>
    </div>
    <!-- 內容摺疊 -->
    <div class="body">
      <div>{{ guide }}</div>
      <Timer
        v-if="excuMin != 0 || excuSec != 0"
        :min="excuMin"
        :sec="excuSec"
        @finishHandler="finishHandler"
      />
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      title: {
        type: String,
        required: true,
      },
      guide: {
        type: String,
      },
      stepCount: {
        type: Number,
        required: true,
      },
      volume: {
        type: Number,
      },
      excuMin: {
        type: Number,
      },
      excuSec: {
        type: Number,
      },
    },
    components: {
      Timer: () => import("@/components/Timer"),
    },
    data() {
      return {
        isFinished: false,
      };
    },
    methods: {
      finishHandler() {
        this.isFinished = true;
      },
    },
  };
</script>

<style>
</style>