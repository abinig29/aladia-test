<template>
  <footer class="bg-[#2D2F31] mt-auto">
    <!-- Top Banner -->
    <div class="border-t border-b border-gray-600">
      <div class="mx-auto px-4 sm:px-6 lg:px-8 py-6">
        <div
          class="flex flex-col md:flex-row justify-between items-center gap-4"
        >
          <p class="text-white text-lg">
            Top companies choose
            <a href="#" class="text-purple-200 hover:text-purple-300 font-bold"
              >Udemy Business</a
            >
            to build in-demand career skills.
          </p>
          <div class="flex items-center gap-8 mr-10 flex-wrap">
            <img
              v-for="company in companies"
              :key="company.name"
              :src="company.logo"
              :alt="company.name"
              class="h-10 object-contain grayscale opacity-60"
            />
          </div>
        </div>
      </div>
    </div>

    <!-- Footer Links -->
    <div class="flex items-start ">
      <div class="px-4 sm:px-6 lg:px-8 py-12 flex-1">
        <div class="grid grid-cols-1 md:grid-cols-3  gap-8 ">
          <div class="space-y-2">
            <a
              v-for="link in column1"
              :key="link.text"
              :href="link.href"
              class="block text-gray-100 hover:text-white"
            >
              {{ link.text }}
            </a>
          </div>
          <div class="space-y-2">
            <a
              v-for="link in column2"
              :key="link.text"
              :href="link.href"
              class="block text-gray-100 hover:text-white"
            >
              {{ link.text }}
            </a>
          </div>
          <div class="space-y-2">
            <a
              v-for="link in column3"
              :key="link.text"
              :href="link.href"
              class="block text-gray-100 hover:text-white"
            >
              {{ link.text }}
            </a>
          </div>
        </div>
      </div>
      <div class="py-12 flex justify-end mr-10 flex-1">
        <button
          class="flex items-center gap-2 px-8 py-2 border border-white text-gray-300 hover:bg-gray-800"
        >
          <GlobeIcon class="h-5 w-5" />
          English
        </button>
      </div>
    </div>

    <!-- Bottom Section -->
    <div class="pb-16 border-gray-700">
      <div class="mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <div
          class="flex flex-col md:flex-row justify-between items-center gap-4"
        >
          <a href="/" class="text-white font-bold text-2xl">
            <img src="/public//images/logo.svg" alt="Udemy" class="h-8" />
          </a>
          <div class="flex items-center gap-4">
            <span class="text-gray-400 text-xs">© 2024 Udemy, Inc.</span>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { GlobeIcon } from "lucide-vue-next";

const companies = [
  { name: "Nasdaq", logo: "/images//nasdaq-light.svg" },
  {
    name: "Volkswagen",
    logo: "/images//volkswagen-light.svg",
  },
  { name: "Box", logo: "/images//box-light.svg" },
  {
    name: "NetApp",
    logo: "/images//netapp-light.svg",
  },
  {
    name: "Eventbrite",
    logo: "/images//eventbrite-light.svg",
  },
];

const column1 = [
  { text: "Udemy Business", href: "#" },
  { text: "Teach on Udemy", href: "#" },
  { text: "Get the app", href: "#" },
  { text: "About us", href: "#" },
  { text: "Contact us", href: "#" },
];

const column2 = [
  { text: "Careers", href: "#" },
  { text: "Blog", href: "#" },
  { text: "Help and Support", href: "#" },
  { text: "Affiliate", href: "#" },
  { text: "Investors", href: "#" },
];

const column3 = [
  { text: "Terms", href: "#" },
  { text: "Privacy policy", href: "#" },
  { text: "Cookie settings", href: "#" },
  { text: "Sitemap", href: "#" },
  { text: "Accessibility statement", href: "#" },
];
</script>
