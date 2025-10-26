<template>
  <header class="bg-white dark:bg-gray-900 border-b border-gray-100 dark:border-gray-700 px-4 sm:px-8 py-4">
    <!-- Desktop Header -->
    <div class="hidden md:flex flex-col md:flex-row md:items-center md:justify-between gap-4">
      <!-- Search -->
      <div
        class="flex items-center bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 rounded-lg px-3 py-2.5 w-full md:w-80"
      >
        <!-- Icon -->
        <img
          src="/img/ui3JuE9Brz.png"
          alt="Search"
          class="w-6 h-4 mr-2 dark:filter dark:invert"
        />
        <!-- Input -->
        <input
          type="text"
          placeholder="Type a command or search..."
          class="flex-1 text-sm text-gray-600 dark:text-gray-300 placeholder-gray-400 dark:placeholder-gray-500 bg-transparent outline-none"
        />
      </div>

      <!-- User Section -->
      <div class="flex items-center justify-between md:justify-end gap-4 w-full md:w-auto">
        <!-- Team Avatars -->
        <div class="flex items-center bg-gray-100 dark:bg-gray-800 rounded-lg p-1 gap-1">
          <img src="/img/u4AmXJ70J5.png" alt="User 1" class="w-9 h-9 rounded" />
          <img src="/img/8y3hDYzTt2.png" alt="User 2" class="w-9 h-9 rounded" />
        </div>

        <!-- Profile -->
        <div class="flex items-center bg-gray-100 dark:bg-gray-800 rounded-lg p-1 gap-1.5">
          <img
            src="/img/6EWEyTrWcK.png"
            alt="Profile"
            class="w-8 h-8 rounded-full"
          />
          <img src="/img/1Ex4OybcD8.png" alt="Dropdown" class="w-4 h-4" />
        </div>
      </div>
    </div>

    <!-- Mobile Header -->
    <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4 md:hidden">
      <div class="flex items-center space-x-3">
        <div
          class="w-10 h-10 bg-blue-500 rounded-full flex items-center justify-center text-white font-bold"
        >
          21
        </div>
        <div>
          <h1 class="font-semibold text-gray-900">Package 1</h1>
          <p class="text-sm text-gray-500">Next billing on May 1, 2025</p>
        </div>
      </div>
      
    </div>
  </header>
</template>

<script setup>
import { computed } from "vue";

const items = computed(() => [
  {
    image: "/assets/img/8o0JvHqFDY.png",
    width: "w-[200px]",
  },
]);
</script>
