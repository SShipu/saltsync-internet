<template>
  <div class="bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-lg p-6">
    <!-- Header -->
    <div class="mb-6">
      <div class="flex items-center justify-between mb-4">
        <h2 class="text-2xl font-semibold text-gray-900 dark:text-white font-inter">My Referral History</h2>
      </div>
      
      <!-- Controls -->
      <div class="flex items-center justify-between">
        <div class="flex items-center gap-2">
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
      </div>
    </div>
    
    <!-- Table -->
    <div class="border border-gray-200 dark:border-gray-700 rounded-2xl overflow-hidden">
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
            <td class="px-6 py-4 text-sm text-gray-900 dark:text-white">{{ row.point }}</td>
          </tr>
        </tbody>
      </table>
      
      <!-- Pagination -->
      <div class="bg-white dark:bg-gray-800 border-t border-gray-200 dark:border-gray-700 px-6 py-4">
        <div class="flex items-center justify-between">
          <span class="text-sm text-gray-600 dark:text-gray-300">1 of 100 row(s) selected.</span>
          
          <div class="flex items-center gap-8">
            <!-- Rows per page -->
            <div class="flex items-center gap-2">
              <span class="text-sm text-gray-700 dark:text-gray-300">Rows per page</span>
              <button class="flex items-center gap-1 border border-gray-300 dark:border-gray-600 rounded-lg px-3 py-2 text-sm text-gray-900 dark:text-white">
                10
                <img src="/img/52njDaMr51.png" alt="Dropdown" class="w-5 h-5">
              </button>
            </div>
            
            <span class="text-sm text-gray-700 dark:text-gray-300">Page 1 of 10</span>
            
            <!-- Navigation -->
            <div class="flex items-center gap-2">
              <button class="w-9 h-9 border border-gray-200 dark:border-gray-600 rounded-lg flex items-center justify-center">
                <img src="/img/rpdwSvKcuK.png" alt="First" class="w-4 h-4">
              </button>
              <button class="w-9 h-9 border border-gray-200 dark:border-gray-600 rounded-lg flex items-center justify-center">
                <img src="/img/phOHJ0vbLp.png" alt="Previous" class="w-4 h-4">
              </button>
              <button class="w-9 h-9 border border-gray-300 dark:border-gray-600 rounded-lg flex items-center justify-center">
                <img src="/img/MPTh8qTJvE.png" alt="Next" class="w-4 h-4">
              </button>
              <button class="w-9 h-9 border border-gray-300 dark:border-gray-600 rounded-lg flex items-center justify-center">
                <img src="/img/aLAxv7eDke.png" alt="Last" class="w-4 h-4">
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import StatusBadge from './StatusBadge.vue'

const tableData = reactive([
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(270) 555-0117', email: 'nathan@gmail.com', status: 'success', discount: '200', point: '200', selected: false },
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(603) 555-0123', email: 'N/A', status: 'pending', discount: 'N/A', point: 'N/A', selected: false },
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(671) 555-0110', email: 'jessica@gmail.com', status: 'rejected', discount: 'N/A', point: 'N/A', selected: false },
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(225) 555-0118', email: 'tanya@gmail.com', status: 'success', discount: '10', point: '100', selected: true },
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(302) 555-0107', email: 'N/A', status: 'success', discount: '10', point: '100', selected: false },
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(209) 555-0104', email: 'nevaeh@gmail.com', status: 'success', discount: '10', point: '100', selected: false },
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(201) 555-0124', email: 'michelle@gmail.com', status: 'success', discount: '10', point: '100', selected: false },
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(239) 555-0108', email: 'sanders@gmail.com', status: 'success', discount: '10', point: '100', selected: false },
  { date: '29 January, 2019', name: 'Forhad Sheikh', phone: '(207) 555-0119', email: 'curtis@gmail.com', status: 'success', discount: '10', point: '100', selected: false },
])
</script>
