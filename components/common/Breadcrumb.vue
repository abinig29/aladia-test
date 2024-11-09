<template>
  <nav class="text-gray-300 mb-6">
    <ol class="flex space-x-1">
      <li v-for="(item, index) in items" :key="index">
        <a
          :href="item.href"
          class="text-blue-400 font-semibold"
          :class="{
            'text-blue-400': index === items.length - 1,
            'hover:text-white': index !== items.length - 1,
          }"
        >
          {{ item.name }}
        </a>
        <ChevronRightIcon
          v-if="index < items.length - 1"
          class="h-5 w-5 inline-block mx-2"
        />
      </li>
    </ol>
  </nav>
</template>

<script setup>
import { ChevronRightIcon } from "lucide-vue-next";

defineProps({
  items: {
    type: Array,
    required: true,
  },
});
</script>
