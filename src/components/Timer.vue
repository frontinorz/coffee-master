<template>
  <div>
    <input
      type="number"
      max="59"
      min="0"
      readonly
      :value="minDisplay"
    >
    <span>分</span>
    <input
      type="number"
      max="59"
      min="0"
      readonly
      :value="secDisplay"
    >
    <span>秒</span>
    <button @click="startHandler">Start</button>
  </div>
</template>

<script>
  export default {
    props: {
      autoStart: {
        type: Boolean,
        default: false,
      },
      min: {
        type: Number,
        default: 0,
      },
      sec: {
        type: Number,
        default: 0,
      },
    },
    data() {
      return {
        minDisplay: 0,
        secDisplay: 0,
        total: 0,
        isTicking: false,
      };
    },
    created() {
      this.total = this.min * 60 + this.sec;
      this.timeDisplay();

      if (this.autoStart) this.startHandler();
    },
    methods: {
      timeDisplay() {
        this.minDisplay = Math.floor(this.total / 60);
        this.secDisplay = this.total % 60;
      },
      startHandler() {
        if (this.isTicking) return;
        this.isTicking = true;
        const tick = setInterval(() => {
          if (this.total <= 0) {
            this.isTicking = false;
            clearInterval(tick);
            this.$emit("finishHandler");
          } else {
            this.total -= 1;
            this.timeDisplay();
          }
        }, 1000);
      },
    },
  };
</script>

<style>
</style>