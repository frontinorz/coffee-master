<template>
  <div
    class="step"
    :class="{'now' : executing}"
  >
    <!-- 執行到的時候下拉 -->
    <div class="header">
      <div>{{ title }}</div>
      <div>{{ isFinished }}</div>
    </div>
    <!-- 內容摺疊 -->
    <div class="body">
      <div>指導: {{ guide }}</div>
      <div>注水量: {{ volume }} ml</div>
      <Timer
        v-if="excuMin != 0 || excuSec != 0"
        :min="excuMin"
        :sec="excuSec"
        :immediately="autoStart && executing"
        @finishHandler="finishHandler"
      />
      <button
        v-else
        @click="finishHandler"
      >下一步</button>
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
      stepNow: {
        type: Number,
        required: true,
      },
      volume: {
        type: Number,
        default: 0,
      },
      excuMin: {
        type: Number,
        default: 0,
      },
      excuSec: {
        type: Number,
        default: 0,
      },
      autoStart: {
        type: Boolean,
        default: false,
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
    computed: {
      executing() {
        return this.stepCount == this.stepNow;
      },
    },
    methods: {
      finishHandler() {
        if (this.isFinished) return;
        this.isFinished = true;
        this.$emit("finishHander");
      },
    },
  };
</script>

<style lang="scss">
  .now {
    color: red;
  }
</style>