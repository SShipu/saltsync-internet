<template>
  <div class="relative">
    <button 
      :class="[
        'w-full flex items-center gap-2 px-3 py-2.5 rounded-xl text-left transition-colors',
        isActive 
          ? 'bg-gradient-to-r from-blue-800 to-gray-900 text-white border border-blue-600/50' 
          : 'text-gray-900 hover:bg-white/20 dark:text-gray-200 dark:hover:bg-gray-700/40'
      ]"
    >
      <img :src="icon" :alt="label" class="w-5 h-5 flex-shrink-0">
      <span class="flex-1 font-medium">{{ label }}</span>
      
      <!-- Badge -->
      <span 
        v-if="badge" 
        class="bg-primary-500 text-white text-xs px-2 py-0.5 rounded-md min-w-[20px] text-center"
      >
        {{ badge }}
      </span>
      
      <!-- Dropdown Arrow -->
      <img 
        v-if="hasDropdown" 
        :src="isActive ? dropdownActiveIcon : dropdownIcon" 
        alt="Dropdown" 
        class="w-5 h-5 flex-shrink-0"
      >
    </button>
  </div>
</template>

<script setup>
import { computed } from 'vue'

// Props
defineProps({
  icon: { type: String, required: true },
  label: { type: String, required: true },
  hasDropdown: { type: Boolean, default: false },
  badge: { type: [String, Number], default: null },
  isActive: { type: Boolean, default: false }
})

// Dropdown icons
const dropdownIcon = '/img/hwoYfwicKg.png'
const dropdownActiveIcon = '/img/2395UgNPPy.png'
</script>
