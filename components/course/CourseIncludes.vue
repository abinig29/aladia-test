<template>
  <div class="my-4">
    <h2 class="text-xl font-bold mb-4">This course includes:</h2>
    <div class="grid lg:grid-cols-2 lg:gap-4 gap-2">
      <div
        v-for="feature in features"
        :key="feature.text"
        class="flex items-center text-gray-900"
      >
        <!-- Use the mapped icon component dynamically -->
        <component :is="icons[feature.icon]" class="lg:h-5 lg:w-5 h-4 w-4 mr-2" />
        <span class="">{{ feature.text }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Video, FileText, Download, Smartphone, Award } from "lucide-vue-next";

defineProps({
  features: {
    type: Array,
    required: true,
  },
});

const icons = {
  Video,
  FileText,
  Download,
  Smartphone,
  Award,
};
</script>
