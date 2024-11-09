<template>
  <div class="my-2">
    <h2 class="text-xl font-bold mb-4">Instructor</h2>
    <a
      :href="instructor.profileUrl"
      class="text-purple-700 hover:text-purple-900 text-lg font-bold underline"
    >
      {{ instructor.name }}
    </a>
    <p class="text-gray-700 mt-1">{{ instructor.title }}</p>
    <div class="flex items-center gap-4 mt-4">
      <img
        :src="instructor.avatar"
        :alt="instructor.name"
        class="w-28 h-28 rounded-full object-cover"
      />
      <div class="grid grid-cols-1 mb-4 text-gray-500">
        <div class="flex items-center gap-2">
          <StarIcon class="h-3 w-3 fill-current text-gray-800" />
          <span>{{ instructor.rating }} Instructor Rating</span>
        </div>
        <div class="flex items-center gap-2">
          <MessageCircleIcon class="h-3 w-3 fill-current text-gray-800" />
          <span>{{ instructor.reviews.toLocaleString() }} Reviews</span>
        </div>
        <div class="flex items-center gap-2">
          <UsersIcon class="h-3 w-3 fill-current text-gray-800" />
          <span>{{ instructor.students.toLocaleString() }} Students</span>
        </div>
        <div class="flex items-center gap-2">
          <PlayCircleIcon class="h-3 w-3 fill-current text-gray-800" />
          <span>{{ instructor.courses }} Courses</span>
        </div>
      </div>
    </div>

    <div class="flex items-start gap-6 mt-4">
      <div class="flex-1">
        <div
          class="text-gray-700 space-y-4"
          :class="{ 'line-clamp-3': !isExpanded }"
        >
          <p>{{ instructor.bio }}</p>
          <div v-if="isExpanded">
            <p>{{ instructor.additionalBio }}</p>
          </div>
        </div>

        <button
          @click="isExpanded = !isExpanded"
          class="mt-2 text-purple-800 hover:text-purple-500 font-bold text-sm"
        >
          {{ isExpanded ? "Show less" : "Show more" }}
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import {
  StarIcon,
  MessageCircleIcon,
  UsersIcon,
  PlayCircleIcon,
} from "lucide-vue-next";

defineProps({
  instructor: {
    type: Object,
    required: true,
  },
});

const isExpanded = ref(false);
</script>
