<template>
  <div class="min-h-screen bg-gray-100 dark:bg-gray-900 flex">
    <!-- Sidebar -->
    <Sidebar />

    <!-- Main Content -->
    <main class="flex-1 p-0 lg:p-6 md:p-4">
      <div class="bg-white dark:bg-gray-800 rounded-2xl border border-gray-200 dark:border-gray-700 min-h-full">
        <!-- Top Bar -->
        <TopBar />

        <!-- Content Body -->
        <div class="p-4 lg:p-8 md:p-6 space-y-6">
          <!-- Referral Section -->
          <ReferralSection />

          <!-- Referral Table -->
          <ReferralTable />
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import Sidebar from './components/Sidebar.vue'
import TopBar from './components/TopBar.vue'
import ReferralSection from './components/ReferralSection.vue'
import ReferralTable from './components/ReferralTable.vue'
</script>
