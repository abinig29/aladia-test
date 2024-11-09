<template>
  <div class="bg-white p-6 my-2 border">
    <h2 class="text-xl font-bold mb-6">Frequently Bought Together</h2>
    <div class="space-y-4">
      <div
        v-for="(course, index) in courses"
        :key="course.id"
        class="flex items-start gap-4"
      >
        <div class=" relative">
          <img
            :src="course.thumbnail"
            :alt="course.title"
            class="w-52 h-28 object-cover"
          />
          <div
            v-if="index < courses.length - 1"
            class="flex items-center justify-center w-12 h-12 z-[10] absolute left-1/2 -translate-x-1/2 bottom-0 translate-y-1/2 shadow-2xl border bg-white rounded-full"
          >
            <PlusIcon class="h-6 w-6 text-gray-900" />
          </div>
        </div>
        <div class="flex-1">
          <h3 class="font-bold max-w-64">{{ course.title }}</h3>
          <p class="text-xs text-gray-600">{{ course.instructor }}</p>
          <div class="flex items-center gap-2 mt-1">
            <span class="text-[#4a381c] font-bold">{{ course.rating }}</span>
            <div class="flex text-[#E59819]">
              <StarIcon
                v-for="i in 5"
                :key="i"
                class="h-4 w-4"
                :class="{ 'text-opacity-50': i > Math.floor(course.rating) }"
              />
            </div>
            <span class="text-gray-600 text-sm"
              >({{ course.ratingCount }})</span
            >
          </div>
          <div class="flex items-center gap-2 mt-1">
            <span
              v-if="course.badge"
              class="px-2 py-0.5 text-xs bg-yellow-100 text-yellow-800 rounded"
            >
              {{ course.badge }}
            </span>
          </div>
        </div>
        <div class="text-right">
          <div class="font-bold">${{ course.price.toFixed(2) }}</div>
          <div class="text-sm text-gray-500 line-through">
            ${{ course.originalPrice.toFixed(2) }}
          </div>
        </div>
      </div>
    </div>

    <div
      class="flex items-center justify-between mt-6 pt-6 border-t border-gray-200"
    >
      <div class="flex items-center">
        <div class="text-sm text-gray-900 mr-2">Total:</div>
        <div class="flex items-center gap-2">
          <span class="text-xl font-bold">${{ total.toFixed(2) }}</span>
          <span class="text-gray-500 line-through"
            >${{ originalTotal.toFixed(2) }}</span
          >
        </div>
      </div>
      <button
        class="px-4 py-3 bg-purple-600 text-white font-bold hover:bg-purple-700"
      >
        Add all to cart
      </button>
    </div>
  </div>
</template>

<script setup>
import { StarIcon, PlusIcon } from "lucide-vue-next";

defineProps({
  courses: {
    required: true,
  },
  total: {
    type: Number,
    required: true,
  },
  originalTotal: {
    type: Number,
    required: true,
  },
});
</script>
