<script setup lang="ts">
import StarRating from "@/components/StarRating.vue"
import Slider from "@vueform/slider"
import { ref } from "vue"
const rating = ref(2.5);
</script>

<template>
  <div class="container m-auto flex flex-col gap-2 items-center">
    <h1 class="text-2xl">StarRating example</h1>
    <p>Single self-contained star rating component without dependencies</p>

    <div class=" flex flex-col items-center gap-4">
      <StarRating :rating="rating" />
      <StarRating :rating="rating" size="3rem" />
      <StarRating :rating="rating" :color='"#5785fb"' size="2rem" />
      <StarRating :rating="rating" :color='"#5785fb"' size="1.5rem" />
    </div>

    <div class="w-96 mt-12">
      <Slider v-model="rating" :min="0" :max="5" :step="-1" :lazy="false" />
    </div>
  </div>
</template>

<style src="@vueform/slider/themes/default.css">

</style>
