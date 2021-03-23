<template>
  <div class="home">
    <Recipe
      v-for="(recipe, index) in recipes"
      :key="index"
      :title="recipe.title"
      :guide="recipe.guide"
      :equipment="recipe.equipment"
      :grind="recipe.grind"
      :coffee="recipe.coffee"
      :water="recipe.water"
      :heat="recipe.heat"
      :steps="recipe.steps"
    />
  </div>
</template>

<script>
  import Recipe from "@/components/Recipe";

  export default {
    name: "Home",
    data() {
      return {
        recipes: [
          {
            title: "康朵V60",
            guide: "台中康朵咖啡",
            equipment: "V60",
            grind: "1Z-E 兩圈半",
            coffee: 20,
            water: 300,
            heat: 92,
            steps: [
              {
                title: "悶蒸",
                guide: "大水中間開始，停留2秒，逐漸向外繞出，再快速繞回中心",
                volume: 30,
                excuMin: 0,
                excuSec: 3,
              },
              {
                title: "第一次注水",
                guide: "10 元硬幣慢速繞圈，大水",
                volume: 150,
                excuMin: 0,
                excuSec: 3,
                autoStart: true,
              },
              {
                title: "第二次注水",
                guide: "定點注水，中水量",
                volume: 150,
              },
              {
                title: "靜置",
                guide: "待下壺滴漏至300cc，取下濾杯",
              },
            ],
          },
        ],
      };
    },
    components: {
      Recipe,
    },
    methods: {
      timeSet(min, sec) {
        console.log(min, sec);
        this.process.push({
          timer: {
            min: min,
            sec: sec,
          },
        });
      },
    },
  };
</script>
