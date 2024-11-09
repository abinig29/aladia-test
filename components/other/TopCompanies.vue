<template>
  <div class=" bg-white  p-6 border">
    <h3 class="font-bold mb-2">
      Top companies offer this course to their employees
    </h3>
    <p class="text-sm text-gray-600 mb-4">
      This course was selected for our collection of top-rated courses trusted
      by businesses worldwide.
      <a href="#" class="text-purple-600 hover:text-purple-700 underline">Learn more</a>
    </p>
    <div class="flex items-center justify-between">
      <img
        v-for="company in companies"
        :key="company.name"
        :src="company.logo"
        :alt="company.name"
        class="h-6 object-contain grayscale opacity-60"
      />
    </div>
  </div>
</template>

<script setup>
defineProps({
  companies: {
    type: Array,
    required: true,
  },
});
</script>
