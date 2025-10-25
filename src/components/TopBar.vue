<template>
  <header class="bg-white dark:bg-gray-900 border-b border-gray-100 dark:border-gray-700 px-8 py-4">
    <div class="flex items-center justify-between">
      <!-- Search -->
      <div class="flex items-center bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 rounded-lg px-3 py-2.5 w-80">
  <!-- Icon -->
  <img 
    src="/img/ui3JuE9Brz.png" 
    alt="Search" 
    class="w-6 h-4 mr-2 dark:filter dark:invert"
  >

  <!-- Input -->
  <input 
    type="text" 
    placeholder="Type a command or search..." 
    class="flex-1 text-sm text-gray-600 dark:text-gray-300 placeholder-gray-400 dark:placeholder-gray-500 bg-transparent outline-none"
  >
</div>

      <!-- User Section -->
      <div class="flex items-center gap-4">
        <!-- Team Avatars -->
        <div class="flex items-center bg-gray-100 dark:bg-gray-800 rounded-lg p-1 gap-1">
          <img src="/img/u4AmXJ70J5.png" alt="User 1" class="w-9 h-9 rounded">
          <img src="/img/8y3hDYzTt2.png" alt="User 2" class="w-9 h-9 rounded">
        </div>
        
        <!-- Profile -->
        <div class="flex items-center bg-gray-100 dark:bg-gray-800 rounded-lg p-1 gap-1.5">
          <img src="/img/6EWEyTrWcK.png" alt="Profile" class="w-8 h-8 rounded-full">
          <img src="/img/1Ex4OybcD8.png" alt="Dropdown" class="w-4 h-4">
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>

import { computed } from 'vue';

const items = computed(() => [
    {
        image: "/assets/img/8o0JvHqFDY.png",
        width: "w-[200px]",
    },
]);
</script>
