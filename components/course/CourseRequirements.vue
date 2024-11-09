<template>
  <div class="my-4">
    <h2 class="text-xl font-bold  mb-4">Requirements</h2>
    <ul class="list-disc list-inside space-y-2 text-sm text-gray-900">
      <li v-for="(requirement, index) in requirements" :key="index">
        {{ requirement }}
      </li>
    </ul>
  </div>
</template>

<script setup>
defineProps({
  requirements: {
    type: Array,
    required: true,
  },
});
</script>
