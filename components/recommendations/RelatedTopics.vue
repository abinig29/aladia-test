<template>
  <div class="my-6">
    <h2 class="text-xl font-bold  mb-4">Explore related topics</h2>
    <div class="flex flex-wrap gap-2">
      <button
        v-for="topic in topics"
        :key="topic"
        class="px-4 py-2 rounded-full border border-gray-900 font-bold  hover:bg-gray-200 transition-colors"
      >
        {{ topic }}
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  topics: {
    type: Array,
    required: true,
  },
});
</script>
