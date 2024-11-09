<template>
  <div class="mt-10">
    <h2 class="text-xl font-bold mb-4">Course content</h2>
    <div class="flex items-center justify-between text-gray-900 mb-4">
      <span
        >{{ content.totalSections }} sections •
        {{ content.totalLectures }} lectures • {{ content.totalLength }} total
        length</span
      >
      <button class="text-[#5F34C8] hover:text-[#6d50ff] text-sm font-bold">
        Expand all sections
      </button>
    </div>

    <div class="">
      <div
        v-for="section in content.sections"
        :key="section.title"
        class="bg-gray-100 border  overflow-hidden"
      >
        <button
          @click="section.expanded = !section.expanded"
          class="w-full px-4 py-3 flex items-center justify-between "
        >
          <div class="flex items-center">
            <ChevronDown
              :class="{ 'transform rotate-180': section.expanded }"
              class="h-4 w-4 mr-2 transition-transform"
            />
            <span class="font-bold flex-1 max-lg:text-sm">{{ section.title }}</span>
          </div>
          <div class="text-sm ">
            {{ section.lectureCount }} lectures • {{ section.duration }}
          </div>
        </button>

        <div v-if="section.expanded" class="border-t bg-white">
          <div
            v-for="lecture in section.lectures"
            :key="lecture.title"
            class="flex items-center px-4 py-3 text-sm"
          >
            <component
              :is="getLectureIcon(lecture.type)"
              class="h-4 w-4 mr-4 text-gray-900"
            />
            <div class="flex-1">
              <div class="flex items-center">
                <span class="text-gray-900">{{ lecture.title }}</span>
                <button
                  v-if="lecture.preview"
                  class="ml-2 text-sm text-purple-400 hover:text-purple-300"
                >
                  Preview
                </button>
              </div>
            </div>
            <span class="text-sm text-gray-400">{{ lecture.duration }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ChevronDown, Play, FileText } from "lucide-vue-next";

defineProps({
  content: {
    type: Object,
    required: true,
  },
});

function getLectureIcon(type) {
  return type === "resource" ? FileText : Play;
}
</script>
