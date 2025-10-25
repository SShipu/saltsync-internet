<template>
  <aside class="w-60 h-screen flex flex-col relative overflow-hidden bg-gray-100 dark:bg-gray-800 transition-colors">
    <!-- Background Gradient -->
    <div class="absolute inset-0 bg-gradient-to-b from-blue-900/20 to-transparent"></div>

    <!-- Header -->
   <header class="p-4 relative z-10">
    <div class="flex items-center justify-between bg-white/10 dark:bg-gray-800 rounded-lg p-2">
        <!-- Logo -->
        <img 
        src="/img/3AvOq45o9E.png" 
        alt="Logo" 
        class="h-7 block dark:hidden"
        >
        <img 
        src="/img/dark-logo.png" 
        alt="Logo Dark" 
        class="h-7 hidden dark:block"
        >

        <!-- Panel Button -->
        <button class="p-1">
        <img src="/img/pvJZdyToey.png" alt="Panel" class="w-4 h-4">
        </button>
    </div>
    </header>


    <!-- Navigation -->
    <nav class="flex-1 px-4 py-2 relative z-10 overflow-y-auto">
      <div class="space-y-8">
        <!-- Platform Section -->
        <div>
          <h3 class="text-gray-600 dark:text-gray-400 text-sm font-medium px-3 py-2">Main</h3>
          <div class="space-y-1">
            <NavItem icon="/img/mRjUJ77CAX.png" label="Home" hasDropdown />
            <NavItem icon="/img/u4pyRz6Dhs.png" label="Offer" hasDropdown />
            <NavItem icon="/img/RpfpWu3jVb.png" label="Package" hasDropdown />
          </div>
        </div>

        <!-- Activity Section -->
        <div>
          <h3 class="text-gray-600 dark:text-gray-400 text-sm font-medium px-3 py-2">Activity</h3>
          <div class="space-y-1">
            <NavItem icon="/img/XPPOcj12o5.png" label="Task" hasDropdown />
            <NavItem 
              icon="/img/x7VVkAKxLk.png" 
              label="Referral" 
              hasDropdown 
              :isActive="true"
            />
            <NavItem icon="/img/5FqfRhKwSt.png" label="Accounting" hasDropdown />
            <NavItem icon="/img/tPzwmmpcJO.png" label="Report" hasDropdown />
          </div>
        </div>

        <!-- Others Section -->
        <div>
          <h3 class="text-gray-600 dark:text-gray-400 text-sm font-medium px-3 py-2">Others</h3>
          <div class="space-y-1">
            <NavItem icon="/img/LqaztYLrxc.png" label="Notification" :badge="8" />
            <NavItem icon="/img/6EWEyTrWcK.png" label="My account" hasDropdown />
          </div>
        </div>
      </div>
    </nav>

    <!-- Footer -->
    <footer class="p-4 space-y-3 relative z-10">
      <!-- Enterprise Plan -->
      <div class="bg-gray-900 rounded-lg p-4">
        <div class="text-gray-300 font-semibold text-sm">Enterprise</div>
        <div class="text-primary-500 text-xs">Next billing on May 1, 2025</div>
      </div>

      <!-- Theme Toggle -->
      <div class="bg-white dark:bg-gray-700 rounded-lg p-1 flex">
        <button 
          @click="setTheme('light')" 
          :class="theme === 'light' ? 'bg-blue-50 text-primary-500' : 'text-gray-600'"
          class="flex-1 flex items-center justify-center gap-2 rounded-lg px-3 py-2 text-sm transition-colors"
        >
          <img src="/img/m1Q18SUzLY.png" alt="Sun" class="w-6 h-6">
          Light
        </button>
        <button 
          @click="setTheme('dark')" 
          :class="theme === 'dark' ? 'bg-blue-900/20 text-white' : 'text-gray-600'"
          class="flex-1 flex items-center justify-center gap-2 rounded-lg px-3 py-2 text-sm transition-colors"
        >
          <img src="/img/xhAAbgo1ir.png" alt="Moon" class="w-6 h-6">
          Dark
        </button>
      </div>
    </footer>
  </aside>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import NavItem from './NavItem.vue'

const theme = ref('light')

const setTheme = (mode) => {
  theme.value = mode
  if (mode === 'dark') {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
  localStorage.setItem('theme', mode)
}

onMounted(() => {
  const savedTheme = localStorage.getItem('theme') || 'light'
  setTheme(savedTheme)
})
</script>

<style>
/* optional smooth color transition */
html {
  transition: background-color 0.3s, color 0.3s;
}
</style>
