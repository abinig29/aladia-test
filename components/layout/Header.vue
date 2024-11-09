<template>
  <nav class="bg-white border-b border-gray-200">
    <div class="mx-auto px-4">
      <div class="flex items-center justify-between h-16">
        <!-- Mobile menu button -->
        <button class="md:hidden p-2 text-gray-700">
          <MenuIcon class="h-6 w-6" />
        </button>

        <!-- Logo -->
        <div class="flex-shrink-0">
          <img
            class="h-8 w-auto"
            src="/public/images/logo-udemy.svg"
            alt="Udemy"
          />
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex flex-1 items-center ml-4">
          <button class="text-gray-700 text-sm">Categories</button>
          <div class="mx-4 flex-1">
            <div class="relative">
              <SearchIcon
                class="absolute left-3 top-1/2 transform -translate-y-1/2 h-5 w-5 text-gray-400"
              />
              <input
                type="search"
                placeholder="Search for anything"
                class="w-full pl-10 pr-4 py-2 border border-gray-900 rounded-full focus:outline-none focus:ring-2 focus:ring-gray-500"
              />
            </div>
          </div>
        </div>

        <!-- Desktop Buttons -->
        <div class="hidden md:flex items-center space-x-4">
          <button class="hidden lg:block text-gray-700 text-sm">Udemy Business</button>
          <button class="text-gray-700 text-sm">Teach on Udemy</button>
          <ShoppingCartIcon class="h-6 w-6 text-gray-700" />
          <button class="px-4 py-2 border border-gray-700 text-gray-700">
            Log in
          </button>
          <button class="px-4 py-2 bg-gray-900 text-white">Sign up</button>
          <button class="px-2 py-2 border border-gray-700">
            <GlobeIcon class="h-6 w-6 text-gray-700" />
          </button>
        </div>

        <!-- Mobile Right Icons -->
        <div class="flex md:hidden items-center space-x-4">
          <button class="p-2 text-gray-700">
            <SearchIcon class="h-6 w-6" />
          </button>
          <button class="p-2 text-gray-700">
            <ShoppingCartIcon class="h-6 w-6" />
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import {
  SearchIcon,
  ShoppingCartIcon,
  GlobeIcon,
  MenuIcon,
} from "lucide-vue-next";
</script>
