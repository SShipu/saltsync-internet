<template>
  <div class="bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-xl p-5 relative overflow-hidden">
    <div class="absolute inset-0 bg-gradient-to-r from-blue-50 dark:from-blue-900/20 to-transparent"></div>
    <div class="relative z-10 flex items-center gap-5">
      <img :src="icon" :alt="title" class="w-12 h-12">
      <div class="flex-1">
        <h3 class="text-gray-600 dark:text-gray-300 font-semibold mb-2">{{ title }}</h3>
        <div class="flex items-center gap-2">
          <span class="text-3xl font-semibold text-gray-900 dark:text-white font-inter">{{ value }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  icon: { type: String, required: true },
  title: { type: String, required: true },
  value: { type: String, required: true }
})
</script>
