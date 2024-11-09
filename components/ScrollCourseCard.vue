<template>
  <div
    v-if="showComponent"
    class="fixed hidden lg:block right-[12%] bg-white shadow-lg border top-8 max-w-[360px] z-[120]"
  >
    <div class="border-b border-gray-200">
      <div class="flex">
        <button
          @click="activeTab = 'personal'"
          class="flex-1 py-4 px-4 text-center font-medium"
          :class="
            activeTab === 'personal'
              ? 'border-b-2 border-black'
              : 'text-gray-500'
          "
        >
          Personal
        </button>
        <button
          @click="activeTab = 'teams'"
          class="flex-1 py-4 px-4 text-center font-medium"
          :class="
            activeTab === 'teams' ? 'border-b-2 border-black' : 'text-gray-500'
          "
        >
          Teams
        </button>
      </div>
    </div>

    <div v-if="activeTab === 'personal'" class="p-6">
      <h2 class="text-xl font-bold mb-2">Subscribe to Udemy's top courses</h2>
      <p class="text-gray-600 mb-2 text-sm">
        Get this course, plus 12,000+ of our top-rated courses, with Personal
        Plan.
        <a
          href="#"
          class="text-purple-600 hover:text-purple-700 underline font-bold"
          >Learn more</a
        >
      </p>

      <button
        class="w-full bg-purple-600 hover:bg-purple-700 text-white py-3 mb-4"
      >
        Try Personal Plan for free
      </button>

      <p class="text-center text-xs text-gray-500 mb-2">
        Starting at $10.00 per month after trial
      </p>
      <p class="text-center text-xs text-gray-500 mb-2">Cancel anytime</p>

      <div class="text-center text-xs text-gray-500 mb-2">or</div>

      <div class="flex items-center gap-2 mb-2">
        <span class="text-2xl font-bold">$10.99</span>
        <span class="line-through text-gray-500">$59.99</span>
        <span class="text-gray-700">82% off</span>
      </div>

      <div class="flex items-center text-red-600 mb-4 text-sm">
        <ClockIcon class="h-4 w-4 mr-1" />
        <span>3 hours left at this price!</span>
      </div>

      <button
        class="w-full border border-gray-900 hover:bg-gray-500/20 text-gray-900 font-bold py-3 mb-4 cursor-pointer"
      >
        Add to cart
      </button>

      <div class="text-center text-sm text-gray-500 mb-4">
        30-Day Money-Back Guarantee
      </div>
      <div class="text-center text-sm text-gray-500 mb-2">
        Full Lifetime Access
      </div>

      <div class="flex justify-between text-sm text-gray-600 mb-4">
        <button class="text-gray-900 font-bold underline">Share</button>
        <button class="text-gray-900 font-bold underline">
          Gift this course
        </button>
        <button class="text-gray-900 font-bold underline">Apply Coupon</button>
      </div>

      <div
        class="bg-gray-50 px-3 py-1 mb-4 flex justify-between items-center border border-dashed"
      >
        <div>
          <div class="font-medium text-gray-500">
            ST2MT110724BNEW <span class="text-sm font-normal">is applied</span>
          </div>
          <div class="text-sm text-gray-500">Udemy coupon</div>
        </div>
        <button class="text-gray-400 hover:text-gray-600">
          <XIcon class="h-5 w-5 text-blue-500" />
        </button>
      </div>

      <div class="flex">
        <input
          type="text"
          placeholder="Enter Coupon"
          class="flex-1 border border-r-0 border-gray-900 px-3 py-2 focus:outline-none focus:ring-1 focus:ring-gray-400"
        />
        <button class="bg-gray-900 text-white px-4 py-2 hover:bg-gray-800">
          Apply
        </button>
      </div>
    </div>

    <div v-if="activeTab === 'teams'" class="p-6">
      <h2 class="font-bold mb-2">
        <span class="text-xl">Udemy</span>
        <span class="text-purple-600">business</span>
      </h2>
      <p class="text-gray-600 mb-4">
        Subscribe to this course and 27,000+ top-rated Udemy courses for your
        organization.
      </p>

      <button
        class="w-full bg-purple-600 hover:bg-purple-700 text-white py-3 rounded mb-6"
      >
        Try Udemy Business
      </button>

      <ul class="space-y-3">
        <li class="flex items-center text-gray-600">
          <CheckIcon class="h-5 w-5 mr-2 text-gray-400" />
          For teams of 2 or more users
        </li>
        <li class="flex items-center text-gray-600">
          <CheckIcon class="h-5 w-5 mr-2 text-gray-400" />
          27,000+ fresh & in-demand courses
        </li>
        <li class="flex items-center text-gray-600">
          <CheckIcon class="h-5 w-5 mr-2 text-gray-400" />
          Learning Engagement tools
        </li>
        <li class="flex items-center text-gray-600">
          <CheckIcon class="h-5 w-5 mr-2 text-gray-400" />
          SSO and LMS Integrations
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { PlayIcon, ClockIcon, CheckIcon, XIcon } from "lucide-vue-next";

defineProps({
  course: {
    type: Object,
    required: true,
  },
});

const activeTab = ref("personal");

const showComponent = ref(false);
const threshold = 950;
const bottomThreshold = 400;

function onScroll() {
  const scrollY = window.scrollY;
  const windowHeight = window.innerHeight;
  const documentHeight = document.documentElement.scrollHeight;

  const distanceFromBottom = documentHeight - (scrollY + windowHeight);

  // Show the component if scrolled past threshold and not within bottom threshold
  showComponent.value =
    scrollY > threshold && distanceFromBottom > bottomThreshold;
}

onMounted(() => {
  window.addEventListener("scroll", onScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", onScroll);
});
</script>
