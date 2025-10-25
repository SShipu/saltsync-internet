<template>
  <span :class="badgeClasses" class="inline-flex items-center px-2 py-1 rounded-full text-xs font-medium">
    {{ statusText }}
  </span>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  status: { type: String, required: true }
})

const badgeClasses = computed(() => {
  switch (props.status) {
    case 'success':
      return 'bg-success-50 dark:bg-success-900 text-success-500 dark:text-success-300 border border-green-200 dark:border-green-700'
    case 'pending':
      return 'bg-warning-50 dark:bg-warning-900 text-warning-500 dark:text-yellow-300 border border-yellow-200 dark:border-yellow-700'
    case 'rejected':
      return 'bg-error-50 dark:bg-error-900 text-error-500 dark:text-red-300 border border-red-200 dark:border-red-700'
    default:
      return 'bg-gray-50 dark:bg-gray-800 text-gray-500 dark:text-gray-300 border border-gray-200 dark:border-gray-700'
  }
})

const statusText = computed(() => {
  switch (props.status) {
    case 'success': return 'Success'
    case 'pending': return 'Pending'
    case 'rejected': return 'Rejected'
    default: return props.status
  }
})
</script>
