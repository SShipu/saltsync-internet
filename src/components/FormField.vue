<template>
  <div class="space-y-2">
    <label class="block text-sm text-gray-900 dark:text-gray-200">
      {{ label }}
      <span v-if="required" class="text-red-500">*</span>
    </label>

    <div v-if="isSelect" class="relative">
      <input 
        type="text" 
        :placeholder="placeholder"
        class="w-full border rounded-lg px-3 py-2.5 text-sm placeholder-gray-500 outline-none 
               border-gray-200 focus:border-primary-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-gray-200"
        readonly
      >
      <img 
        src="/img/eyjryuvpDN.png" 
        alt="Dropdown" 
        class="absolute right-3 top-1/2 transform -translate-y-1/2 w-5 h-5"
      >
    </div>

    <input 
      v-else
      type="text" 
      :placeholder="placeholder"
      class="w-full border rounded-lg px-3 py-2.5 text-sm placeholder-gray-500 outline-none 
             border-gray-200 focus:border-primary-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-gray-200"
    >
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// Props
defineProps({
  label: { type: String, required: true },
  placeholder: { type: String, required: true },
  required: { type: Boolean, default: false },
  isSelect: { type: Boolean, default: false },
  apiUrl: { type: String, default: null } // optional API endpoint
})

// Dark mode reactive handling
const theme = ref('light')
const setTheme = (mode) => {
  theme.value = mode
  if (mode === 'dark') document.documentElement.classList.add('dark')
  else document.documentElement.classList.remove('dark')
  localStorage.setItem('theme', mode)
}

// Initialize theme on mount
onMounted(() => {
  const savedTheme = localStorage.getItem('theme') || 'light'
  setTheme(savedTheme)
})
</script>
