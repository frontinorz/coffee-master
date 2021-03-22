<template>
  <div>
    <div>
      <div>手法: {{ title }}</div>
      <div>設備: {{ equipment }}</div>
      <div>豆量: {{ coffee }}</div>
      <div>水量: {{ water }}</div>
      <div>研磨度: {{ grind }}</div>
      <div>水溫 : {{ heat }}</div>
    </div>
    <Step
      v-for="(step,index) in steps"
      :key="index"
      :stepCount="index + 1"
      :title="step.title"
      :guide="step.guide"
      :excuMin="step.excuMin"
      :excuSec="step.excuSec"
    />
  </div>
</template>

<script>
  import Step from "@/components/Step";
  export default {
    props: {
      title: {
        type: String,
        required: true,
      },
      equipment: {
        type: String,
        required: true,
      },
      coffee: {
        type: Number,
        required: true,
      },
      water: {
        type: Number,
        required: true,
      },
      grind: {
        type: String,
      },
      heat: {
        type: Number,
      },
      steps: {
        type: Array,
      },
    },
    data() {
      return {};
    },
    components: {
      Step,
    },
  };
</script>

<style>
</style>