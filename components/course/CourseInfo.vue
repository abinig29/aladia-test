<template>
  <div>
    <h1 class="xl:text-4xl lg:text-3xl md:text-2xl font-bold text-white mb-4 max-w-3xl">
      {{ course.title }}
    </h1>
    <p class="text-gray-300 mb-4">
      {{ course.description }}
    </p>

    <div class="flex items-center space-x-4 mb-6">
      <div class="flex items-center">
        <span class="text-[#E59819] font-bold">{{ course.rating }}</span>
        <div class="flex text-[#E59819] ml-2">
          <StarIcon
            v-for="i in 5"
            :key="i"
            class="h-5 w-5"
            :class="{ 'text-opacity-50': i > Math.floor(course.rating) }"
          />
        </div>
        <span class="text-[#8B8B8B] ml-2"
          >({{ course.ratingCount }} ratings)</span
        >
      </div>
      <span class="text-[#8B8B8B]">{{ course.studentCount }} students</span>
    </div>

    <div class="text-gray-300 mb-8">
      <p>
        Created by
        <a href="#" class="text-[#2d73bd] underline hover:text-white">{{
          course.instructor
        }}</a>
      </p>
      <div class="flex items-center space-x-4 mt-2">
        <div class="flex items-center">
          <ClockIcon class="h-5 w-5 mr-2" />
          <span>Last updated {{ course.lastUpdated }}</span>
        </div>
        <div class="flex items-center gap-2 text-sm">
          <GlobeIcon class="h-5 w-5 mr-2" />
          <span>{{ course.language }}</span>
          <GlobeIcon class="h-5 w-5 mr-2" />
          <span>{{ course.language }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { StarIcon, ClockIcon, GlobeIcon } from "lucide-vue-next";

defineProps({
  course: {
    type: Object,
    required: true,
  },
});
</script>
