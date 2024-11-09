<template>
  <div class="lg:mt-12 bg-white  p-6 border border-gray-300 ">
    <h2 class="text-2xl font-bold mb-6">What you'll learn</h2>
    <div class="grid lg:grid-cols-2 gap-4">
      <div
        v-for="(point, index) in learningPoints"
        :key="index"
        class="flex items-start"
      >
        <CheckIcon  class=" text-gray-900 mr-2 w-10 " />
        <p class="text-sm">{{ point }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { CheckIcon } from "lucide-vue-next";

defineProps({
  learningPoints: {
    type: Array,
    required: true,
  },
});
</script>
