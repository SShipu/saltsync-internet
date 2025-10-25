<template>
  <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
    <!-- Referral Card -->
    <div class="lg:col-span-1">
      <div class="bg-gray-900 dark:bg-gray-800 rounded-2xl p-8 text-white relative overflow-hidden">
        <!-- Background Gradient -->
        <div class="absolute inset-0 bg-gradient-to-br from-blue-600/30 to-transparent"></div>

        <div class="relative z-10 space-y-8">
          <h2 class="text-2xl font-bold leading-tight">
            Refried friend and Get ৳10 off. Get up to ৳600.
          </h2>

          <div class="space-y-4">
            <!-- Referral Link -->
            <div>
              <label class="block text-white text-sm mb-2">Your referral invite link</label>
              <div class="flex gap-2">
                <div class="flex-1 bg-white dark:bg-gray-700 rounded-lg px-3 py-2.5">
                  <span class="text-gray-600 dark:text-gray-300 text-sm">saltsync.com/EApVptt1jL3</span>
                </div>
                <button class="bg-white dark:bg-gray-700 text-gray-700 dark:text-gray-200 px-4 py-2.5 rounded-lg text-sm font-medium border border-gray-300 dark:border-gray-600">
                  Copy Link
                </button>
              </div>
            </div>

            <!-- Share Options -->
            <div>
              <label class="block text-white text-sm mb-2">Share with</label>
              <div class="flex gap-2.5">
                <button class="w-10 h-10 bg-white dark:bg-gray-700 rounded-lg border border-gray-300 dark:border-gray-600 flex items-center justify-center">
                  <img src="/img/qTz95tLWhN.png" alt="Share 1" class="w-6 h-6">
                </button>
                <button class="w-10 h-10 bg-white dark:bg-gray-700 rounded-lg border border-gray-300 dark:border-gray-600 flex items-center justify-center">
                  <img src="/img/Z1HG36z5Wr.png" alt="Share 2" class="w-6 h-6">
                </button>
                <button class="w-10 h-10 bg-white dark:bg-gray-700 rounded-lg border border-gray-300 dark:border-gray-600 flex items-center justify-center">
                  <img src="/img/wjmupAnB8e.png" alt="Share 3" class="w-6 h-6">
                </button>
                <button class="w-10 h-10 bg-white dark:bg-gray-700 rounded-lg border border-gray-300 dark:border-gray-600 flex items-center justify-center">
                  <img src="/img/hzhtjtyywH.png" alt="Share 4" class="w-6 h-6">
                </button>
              </div>
            </div>
          </div>

          <button
            class="w-full bg-primary-500 text-white py-3 rounded-lg font-medium"
            @click.prevent="showModal = true"
          >
            Request for New Connection
          </button>
        </div>
      </div>
    </div>

    <!-- Stats Grid -->
    <div class="lg:col-span-2 space-y-6">
      <!-- Reward Points -->
      <div class="bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-xl p-5 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-r from-blue-50 dark:from-gray-700 to-transparent"></div>
        <div class="relative z-10 flex items-center gap-5">
          <div class="text-6xl">🏆</div>
          <div class="flex-1">
            <h3 class="text-gray-600 dark:text-gray-300 text-xl mb-2">Reward Point</h3>
            <div class="flex items-end gap-2">
              <span class="text-4xl font-semibold text-gray-900 dark:text-white font-inter">200</span>
              <span class="text-2xl text-gray-600 dark:text-gray-300 mb-1">৳ 2000</span>
            </div>
          </div>
          <button class="bg-primary-500 text-white px-4 py-2 rounded-lg text-sm font-medium">
            Upgrade
          </button>
        </div>
      </div>

      <!-- Stats Row -->
      <div class="grid grid-cols-2 gap-6">
        <StatCard
          icon="/img/nxBauLHVDY.png"
          title="Total Referral"
          value="20"
        />
        <StatCard
          icon="/img/uSLnBpKKkP.png"
          title="Total Success"
          value="16"
        />
      </div>

      <!-- Bottom Stats Row -->
      <div class="grid grid-cols-2 gap-6">
        <StatCard
          icon="/img/PRHaRQBuf2.png"
          title="Total Pending"
          value="4"
        />
        <StatCard
          icon="/img/gP5wwXuFKC.png"
          title="Total Rejected"
          value="0"
        />
      </div>
    </div>

    <!-- Modal -->
    <ReferralModal v-if="showModal" @close="showModal = false" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import StatCard from './StatCard.vue'
import ReferralModal from './ReferralModal.vue'

const showModal = ref(false)
</script>
