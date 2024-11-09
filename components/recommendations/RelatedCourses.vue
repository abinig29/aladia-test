<template>
  <div class="my-2">
    <h2 class="text-xl font-bold mb-4">Students also bought</h2>
    <div class="space-y-4">
      <div
        v-for="course in courses"
        :key="course.id"
        class="flex gap-6 border-b pb-4"
      >
        <img
          :src="course.thumbnail"
          :alt="course.title"
          class="w-16 h-16 object-cover"
        />
        <div class="flex-1 flex items-start">
          <div>
            <h3 class="font-bold max-w-64">{{ course.title }}</h3>
            <div class="flex items-center text-sm gap-2 text-gray-900 mt-1">
              <div
                class="bg-[#e9c288] px-2 font-semibold text-[#513a17]"
                v-if="course.isHighlyRated"
              >
                Highly rated
              </div>
              <span class="text-[#2d8877] font-bold">{{
                course.totalHours
              }}</span>
              <span>•</span>
              <span>Updated {{ course.lastUpdated }}</span>
            </div>
          </div>
          <div class="flex items-center gap-2 mt-2 flex-1">
            <div class="flex items-center flex-1">
              <span class="text-[#E59819] font-bold">{{ course.rating }}</span>
              <div class="flex text-[#E59819] ml-1">
                <StarIcon class="h-4 w-4 fill-current" />
              </div>
            </div>
            <span class="text-gray-700 flex items-center flex-1 gap-2">
              <Users class="fill-current h-4 w-4" />
              {{ course.students.toLocaleString() }}
            </span>
          </div>
          <div class="flex items-center justify-between mt-2 flex-1">
            <div class="flex items-center text-sm flex-col flex-1">
              <span class="font-bold">${{ course.price.toFixed(2) }}</span>
              <span class="line-through text-gray-400"
                >${{ course.originalPrice.toFixed(2) }}</span
              >
            </div>
            <button
              class="text-gray-400 border rounded-full p-2 border-gray-500"
              @click="toggleWishlist(course.id)"
            >
              <Heart
                :class="{ 'fill-current': course.isWishlisted }"
                class="h-5 w-5"
              />
            </button>
          </div>
        </div>
      </div>
    </div>
    <button
      @click="showMore"
      class="w-full mt-4 py-2 font-bold border border-gray-900 text-gray-800  hover:bg-gray-200 transition-colors"
    >
      Show more
    </button>
  </div>
</template>

<script setup>
import { StarIcon, Heart, Users } from "lucide-vue-next";

const props = defineProps({
  courses: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["toggleWishlist", "showMore"]);

function toggleWishlist(courseId) {
  emit("toggleWishlist", courseId);
}

function showMore() {
  emit("showMore");
}
</script>
