<template>
  <div class="my-4">
    <h2 class="text-xl font-bold  mb-4">Description</h2>
    <div
      class="text-gray-900 space-y-4"
      :class="{ 'line-clamp-3': !isExpanded }"
    >
      <p>
        Learn to
        <strong>design outstanding mobile apps! Impressive prototypes</strong>
        that look like the real deal but <strong>without any coding</strong>.
        This course is a masterclass – a comprehensive approach to mobile app
        designing. I'll teach you everything you need to know, from A to Z.
        We'll use <strong>Figma</strong>. I've taught over 270,000 students on
        Udemy and I'm a best-selling instructor!
      </p>
      <p>
        You'll learn about <strong>Material Design</strong>, the principles of
        color, spacing, and typography, tips and tricks, how to get design
        resources, and much more! Get a life skill that's high in demand in
        today's job market, all for the price of a fancy coffee. Create
        beautiful apps and supercharge your career!
      </p>
      <div v-if="isExpanded">
        <p>You'll learn to:</p>
        <ul class="list-disc list-inside pl-4 space-y-2">
          <li>Design beautiful mobile apps</li>
          <li>Create impressive prototypes</li>
          <li>Master Figma for mobile design</li>
          <li>Understand Material Design principles</li>
        </ul>
      </div>
    </div>
    <button
      @click="isExpanded = !isExpanded"
      class="mt-4 text-purple-800 hover:text-purple-900 font-bold text-sm "
    >
      {{ isExpanded ? "Show less" : "Show more" }}
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isExpanded = ref(false);
</script>
