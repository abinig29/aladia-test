<template>
  <div
    v-show="isVisible"
    class="fixed sm:block hidden sm:bottom-0 h-fit  lg:top-0 left-0 right-0 z-[120] bg-[#1C1D1F] border-b border-gray-700 transform transition-transform duration-300"
    :class="{ '-translate-y-full': !isVisible }"
  >
    <div class="px-4 sm:px-6 lg:px-8 py-2">
      <div class="flex items-center justify-between">
        <div class="flex items-start flex-col">
          <h1 class="text-white font-bold text-sm  line-clamp-1">
            Figma for Mobile App Design: Ultimate Edition
          </h1>
          <div class="flex items-center gap-2 ">
            <span class="text-[#E59819] font-bold">4.7</span>
            <div class="flex text-[#E59819]">
              <StarIcon class="h-4 w-4 fill-current" />
            </div>
            <a
              href="#reviews"
              class="text-[#4d67edba] hover:text-[#2944cbf9]/80 underline"
            >
              (186 ratings)
            </a>
            <span class="text-gray-400">1495 students</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { StarIcon } from "lucide-vue-next";

const props = defineProps({
  threshold: {
    type: Number,
    default: 50,
  },
});

const isVisible = ref(false);

function checkScroll() {
  isVisible.value = window.scrollY > props.threshold;
}

onMounted(() => {
  window.addEventListener("scroll", checkScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", checkScroll);
});
</script>
