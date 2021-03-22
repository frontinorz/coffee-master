<template>
  <div class="home">
    <Recipe
      v-for="(recipe, index) in recipes"
      :key="index"
      :title="recipe.title"
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
            equipment: "V60",
            grind: "1Z-E 兩圈半",
            coffee: 20,
            water: 300,
            heat: 92,
            steps: [
              {
                title: "悶蒸",
                guide: "大水中間開始，停留2秒，逐漸向外繞出，再快速繞回中心",
                volumn: 30,
                excuMin: 0,
                excuSec: 20,
              },
              {
                title: "注水",
                guide: "10 元硬幣慢速繞圈，大水",
                volumn: 150,
              },
              {
                title: "注水",
                guide: "定點注水，中水量",
                volumn: 150,
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
