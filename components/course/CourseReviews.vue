<template>
  <div class="my-6">
    <div class="flex items-center gap-2 mb-6">
      <StarIcon class="h-6 w-6 text-[#E59819] fill-current" />
      <span class="text-2xl font-bold">{{ rating }} course rating</span>
      <span class="text-2xl font-bold">• {{ totalRatings }} ratings</span>
    </div>

    <div class="gap-4 grid lg:grid-cols-2 w-full">
      <div
        v-for="review in reviews"
        :key="review.id"
        class="py-4 h-full border-t"
      >
        <div class="flex items-start justify-between">
          <div class="flex items-center gap-3">
            <div
              class="flex items-center justify-center w-10 h-10 bg-gray-900 text-white rounded-full font-medium"
            >
              {{ getInitials(review.name) }}
            </div>
            <div>
              <h3 class="font-medium">{{ review.name }}</h3>
              <div class="flex items-center gap-2 mt-1">
                <div class="flex text-[#E59819]">
                  <StarIcon
                    v-for="i in 5"
                    :key="i"
                    class="h-3 w-3 fill-current"
                    :class="{
                      'text-opacity-50': i > Math.floor(review.rating),
                    }"
                  />
                </div>
                <span class="text-gray-800 text-sm">{{ review.timeAgo }}</span>
              </div>
            </div>
          </div>
          <button class="text-gray-900">
            <MoreVerticalIcon class="h-5 w-5" />
          </button>
        </div>

        <p class="text-gray-900 font-semibold mt-4">{{ review.content }}</p>

        <div class="flex items-center gap-4 mt-4">
          <div class="text-sm text-gray-400 capitalize">helpful?</div>
          <button
            class="flex items-center gap-1 text-gray-400"
            @click="handleHelpful(review.id, true)"
          >
            <ThumbsUpIcon class="h-4 w-4" />
            <span>{{ review.helpfulCount }}</span>
          </button>
          <button
            class="flex items-center gap-1 text-gray-400"
            @click="handleHelpful(review.id, false)"
          >
            <ThumbsDownIcon class="h-4 w-4" />
          </button>
        </div>
      </div>
    </div>
    <button class="border px-4 py-2 font-bold text-sm border-black">
      Show all reviews
    </button>
  </div>
</template>

<script setup>
import {
  StarIcon,
  MoreVerticalIcon,
  ThumbsUpIcon,
  ThumbsDownIcon,
} from "lucide-vue-next";

const props = defineProps({
  rating: {
    type: Number,
    required: true,
  },
  totalRatings: {
    type: Number,
    required: true,
  },
  reviews: {
    type: Array,
    required: true,
  },
});
function getInitials(name) {
  const nameParts = name.split(" ");
  const initials = nameParts
    .map((part) => part.charAt(0).toUpperCase())
    .join("");
  return initials;
}

const emit = defineEmits(["helpful"]);

function handleHelpful(reviewId, isHelpful) {
  emit("helpful", { reviewId, isHelpful });
}
</script>
