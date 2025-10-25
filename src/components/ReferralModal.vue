<template>
  <div class="fixed inset-0 bg-black/70 flex justify-end z-50">
    <div class="w-[510px] bg-white dark:bg-gray-900 h-full flex flex-col relative overflow-hidden">
      
      <!-- Background Gradient -->
      <div class="absolute top-0 left-0 right-0 h-92 bg-gradient-to-br from-blue-600/20 to-transparent"></div>
      
      <!-- Header -->
      <header class="relative z-10 p-6 flex items-center justify-between">
        <h1 class="text-2xl font-semibold font-inter text-gray-900 dark:text-gray-200">
          New Connection Referred
        </h1>
        <button @click="closeModal" class="w-8 h-8 flex items-center justify-center">
          <img src="/img/r301dYeA1O.png" alt="Close" class="w-8 h-8">
        </button>
      </header>
      
      <!-- Form -->
      <div class="flex-1 px-10 py-6 relative z-10 space-y-4">
        <FormField label="Name" placeholder="Enter name" required />
        <FormField label="Phone" placeholder="Enter phone number" required />
        <FormField label="Email" placeholder="Enter email address" required />
        <FormField label="District Name" placeholder="Select district name" required isSelect />
        <FormField label="Upazilla Name" placeholder="Select upazilla name" required isSelect />
        <FormField label="Address" placeholder="Enter address" required />
        <FormField label="Package Name" placeholder="Select package" required isSelect />
        
        <button class="w-full bg-primary-500 text-white py-3 rounded-lg font-medium mt-8 hover:bg-primary-600 transition-colors">
          Request for New Connection
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import FormField from './FormField.vue'

// Emit close event
const emit = defineEmits(['close'])
const closeModal = () => emit('close')
</script>
