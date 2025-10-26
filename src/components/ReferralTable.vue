<template>
  <div class="w-full flex flex-col gap-4">
    <!-- Header & Controls -->
    <div class="bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-lg p-4 sm:p-6">
      <div class="flex items-center justify-between mb-4">
        <h2 class="text-lg sm:text-2xl font-semibold text-gray-900 dark:text-white font-inter">My Referral History</h2>

        <!-- Desktop Controls -->
        <div class="hidden sm:flex items-center gap-2">
          <!-- Search -->
          <div class="flex items-center bg-white dark:bg-gray-700 border border-gray-200 dark:border-gray-600 rounded-lg px-3 py-2">
            <img src="/img/Q9gbT6tNXT.png" alt="Search" class="w-5 h-5 mr-2">
            <input 
              type="text" 
              placeholder="Search" 
              class="text-sm text-gray-600 dark:text-gray-200 placeholder-gray-400 dark:placeholder-gray-500 outline-none bg-transparent"
            >
          </div>

          <!-- Status Filter -->
          <button class="flex items-center gap-2 border-2 border-dashed border-gray-200 dark:border-gray-600 rounded-lg px-3 py-2 text-sm text-gray-900 dark:text-gray-200">
            <img src="/img/rnRemCktde.png" alt="Plus" class="w-4 h-4">
            Status
          </button>
        </div>

        <!-- Mobile Controls -->
        <div class="flex sm:hidden space-x-2">
          <button class="p-2 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-lg">
            <svg class="w-5 h-5 text-gray-600 dark:text-gray-300" fill="currentColor" viewBox="0 0 24 24">
              <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
            </svg>
          </button>
          <button class="p-2 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-lg">
            <svg class="w-5 h-5 text-gray-600 dark:text-gray-300" fill="currentColor" viewBox="0 0 24 24">
              <path d="M3 18h6v-2H3v2zM3 6v2h18V6H3zm0 7h12v-2H3v2z"/>
            </svg>
          </button>
        </div>
      </div>

      <!-- Desktop Table -->
      <div class="hidden sm:block border border-gray-200 dark:border-gray-700 rounded-2xl overflow-hidden">
        <table class="w-full">
          <thead class="bg-gray-50 dark:bg-gray-700">
            <tr>
              <th class="px-6 py-3 text-left">
                <div class="flex items-center gap-3">
                  <input type="checkbox" class="w-5 h-5 border border-gray-300 dark:border-gray-600 rounded">
                  <span class="text-sm font-semibold text-gray-900 dark:text-white font-inter">Date</span>
                </div>
              </th>
              <th class="px-6 py-3 text-left text-sm font-semibold text-gray-900 dark:text-white font-inter">Name</th>
              <th class="px-6 py-3 text-left text-sm font-semibold text-gray-900 dark:text-white font-inter">Phone</th>
              <th class="px-6 py-3 text-left text-sm font-semibold text-gray-900 dark:text-white font-inter">Email</th>
              <th class="px-6 py-3 text-left text-sm font-semibold text-gray-900 dark:text-white font-inter">Status</th>
              <th class="px-6 py-3 text-left text-sm font-semibold text-gray-900 dark:text-white font-inter">Discount</th>
              <th class="px-6 py-3 text-left text-sm font-semibold text-gray-900 dark:text-white font-inter">Point</th>
            </tr>
          </thead>
          <tbody class="divide-y divide-gray-200 dark:divide-gray-700">
            <tr v-for="(row, index) in tableData" :key="index" :class="{ 'bg-gray-50 dark:bg-gray-700': row.selected }">
              <td class="px-6 py-4">
                <div class="flex items-center gap-3">
                  <input type="checkbox" v-model="row.selected" class="w-4 h-4 border border-gray-300 dark:border-gray-600 rounded">
                  <span class="text-sm text-gray-900 dark:text-white">{{ row.date }}</span>
                </div>
              </td>
              <td class="px-6 py-4 text-sm text-gray-900 dark:text-white">{{ row.name }}</td>
              <td class="px-6 py-4 text-sm text-gray-900 dark:text-white">{{ row.phone }}</td>
              <td class="px-6 py-4 text-sm text-gray-900 dark:text-white">{{ row.email }}</td>
              <td class="px-6 py-4">
                <StatusBadge :status="row.status" />
              </td>
              <td class="px-6 py-4 text-sm text-gray-900 dark:text-white">{{ row.discount }}</td>
              <td class="px-6 py-4 text-sm text-gray-900 dark:text-white">{{ row.points }}</td>
            </tr>
          </tbody>
        </table>

        <!-- Pagination -->
        <div class="bg-white dark:bg-gray-800 border-t border-gray-200 dark:border-gray-700 px-6 py-4">
          <div class="flex items-center justify-between">
            <span class="text-sm text-gray-600 dark:text-gray-300">{{ tableData.length }} row(s) selected.</span>
            <div class="flex items-center gap-2">
              <button class="w-9 h-9 border border-gray-300 dark:border-gray-600 rounded-lg flex items-center justify-center">‹</button>
              <button class="w-9 h-9 border border-gray-300 dark:border-gray-600 rounded-lg flex items-center justify-center">›</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Mobile Cards -->
      <div class="sm:hidden space-y-2">
        <div 
          v-for="item in tableData" 
          :key="item.date + item.name"
          class="bg-white dark:bg-gray-800 rounded-2xl p-4 shadow-sm flex justify-between items-center"
        >
          <div class="flex items-center space-x-3">
            <div class="w-8 h-8 rounded-lg flex items-center justify-center"
                 :class="item.status === 'success' ? 'bg-blue-100 dark:bg-blue-900' : 'bg-gray-100 dark:bg-gray-700'">
              <svg v-if="item.status === 'success'" class="w-4 h-4 text-blue-600 dark:text-blue-400" fill="currentColor" viewBox="0 0 24 24">
                <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
              </svg>
              <svg v-else class="w-4 h-4 text-gray-400 dark:text-gray-300" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-2h2v2zm0-4h-2V7h2v6z"/>
              </svg>
            </div>
            <div>
              <p class="font-medium text-gray-900 dark:text-white text-sm">{{ item.name }}</p>
              <p class="text-xs text-gray-500 dark:text-gray-400">{{ item.date }} // {{ item.time }}</p>
            </div>
          </div>
          <div class="text-right">
            <p class="font-semibold text-gray-900 dark:text-white">৳ {{ item.points }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import StatusBadge from './StatusBadge.vue'

// Local sample data
const tableData = reactive([
  { date: '29 Jan 2025', time: '10:00 AM', name: 'Forhad Sheikh', phone: '017-555-0117', email: 'nathan@gmail.com', status: 'success', discount: '200', points: '200', selected: false },
  { date: '29 Jan 2025', time: '11:00 AM', name: 'Tanya Smith', phone: '019-555-0123', email: 'tanya@gmail.com', status: 'pending', discount: 'N/A', points: 'N/A', selected: false },
  { date: '29 Jan 2025', time: '12:00 PM', name: 'Jessica Lee', phone: '018-555-0110', email: 'jessica@gmail.com', status: 'rejected', discount: 'N/A', points: 'N/A', selected: false },
])
</script>
