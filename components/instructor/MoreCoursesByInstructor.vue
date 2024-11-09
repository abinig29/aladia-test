<template>
  <div class="my-6">
    <h2 class="text-2xl font-bold  mb-6">
      More Courses by
      <a :href="instructorUrl" class="text-purple-800 hover:text-purple-700">
        {{ instructorName }}
      </a>
    </h2>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <div
        v-for="course in courses"
        :key="course.id"
        class=" overflow-hidden transition-colors"
      >
        <a :href="course.url" class="block">
          <img
            :src="course.thumbnail"
            :alt="course.title"
            class="w-full aspect-video object-cover"
          />

          <div class=" mt-2">
            <h3 class="font-bold   mb-1 line-clamp-2">
              {{ course.title }}
            </h3>

            <p class="text-gray-400 text-sm ">{{ course.instructor }}</p>

            <div class="flex items-center gap-2 ">
              <span class="text-[#E59819] font-bold">{{ course.rating }}</span>
              <div class="flex text-[#E59819]">
                <StarIcon
                  v-for="i in 5"
                  :key="i"
                  class="h-4 w-4"
                  :class="{ 'text-opacity-50': i > Math.floor(course.rating) }"
                />
              </div>
              <span class="text-gray-400 text-sm"
                >({{ course.ratingCount }})</span
              >
            </div>

            <div class="text-xs text-gray-400 mb-3">
              {{ course.totalHours }}  •
              {{ course.totalLectures }} • {{ course.level }}
            </div>

            <div class="flex items-center gap-2">
              <span class=" font-bold"
                >${{ course.price.toFixed(2) }}</span
              >
              <span class="text-gray-400 line-through"
                >${{ course.originalPrice.toFixed(2) }}</span
              >
            </div>
          </div>
        </a>
      </div>
    </div>

    <div class="mt-8 text-center">
      <button
        @click="reportAbuse"
        class="text-gray-900 font-bold hover:bg-gray-200 text-sm border border-black w-full py-3"
      >
        Report abuse
      </button>
    </div>
  </div>
</template>

<script setup>
import { StarIcon } from "lucide-vue-next";

defineProps({
  instructorName: {
    type: String,
    required: true,
  },
  instructorUrl: {
    type: String,
    required: true,
  },
  courses: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["reportAbuse"]);

function reportAbuse() {
  emit("reportAbuse");
}
</script>
