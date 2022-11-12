<template>
  <div>
    <v-app id="inspire">
      <all-food-list></all-food-list>
    </v-app>
  </div>
</template>

<script>
import foodCard from "@/views/HomeView/components/foodCard";
import foodCarousel from "@/views/HomeView/components/foodCarousel";
import allFoodList from "@/views/HomeView/allFoodList";
export default {
  name: "HomeView",
  components:{foodCard,foodCarousel,allFoodList},

}
</script>

<style lang="scss" scoped>

</style>
