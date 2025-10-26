<template>
  <div>
    <!-- Desktop Sidebar -->
    <aside
      class="hidden md:flex w-60 h-screen flex-col relative overflow-hidden bg-gray-100 dark:bg-gray-800 transition-colors"
    >
      <!-- Background Gradient -->
      <div
        class="absolute inset-0 bg-gradient-to-b from-blue-900/20 to-transparent"
      ></div>

      <!-- Header -->
      <header class="p-4 relative z-10">
        <div
          class="flex items-center justify-between bg-white/10 dark:bg-gray-800 rounded-lg p-2"
        >
          <!-- Logo -->
          <img
            src="/img/3AvOq45o9E.png"
            alt="Logo"
            class="h-7 block dark:hidden"
          />
          <img
            src="/img/dark-logo.png"
            alt="Logo Dark"
            class="h-7 hidden dark:block"
          />

          <!-- Panel Button -->
          <button class="p-1">
            <img src="/img/pvJZdyToey.png" alt="Panel" class="w-4 h-4" />
          </button>
        </div>
      </header>

      <!-- Navigation -->
      <nav
        class="flex-1 px-4 py-2 relative z-10 overflow-y-auto"
      >
        <div class="space-y-8">
          <!-- Platform Section -->
          <div>
            <h3
              class="text-gray-600 dark:text-gray-400 text-sm font-medium px-3 py-2"
            >
              Main
            </h3>
            <div class="space-y-1">
              <NavItem icon="/img/mRjUJ77CAX.png" label="Home" hasDropdown />
              <NavItem icon="/img/u4pyRz6Dhs.png" label="Offer" hasDropdown />
              <NavItem icon="/img/RpfpWu3jVb.png" label="Package" hasDropdown />
            </div>
          </div>

          <!-- Activity Section -->
          <div>
            <h3
              class="text-gray-600 dark:text-gray-400 text-sm font-medium px-3 py-2"
            >
              Activity
            </h3>
            <div class="space-y-1">
              <NavItem icon="/img/XPPOcj12o5.png" label="Task" hasDropdown />
              <NavItem
                icon="/img/x7VVkAKxLk.png"
                label="Referral"
                hasDropdown
                :isActive="activeTab === 'Referral'"
              />
              <NavItem icon="/img/5FqfRhKwSt.png" label="Accounting" hasDropdown />
              <NavItem icon="/img/tPzwmmpcJO.png" label="Report" hasDropdown />
            </div>
          </div>

          <!-- Others Section -->
          <div>
            <h3
              class="text-gray-600 dark:text-gray-400 text-sm font-medium px-3 py-2"
            >
              Others
            </h3>
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
            <img src="/img/m1Q18SUzLY.png" alt="Sun" class="w-6 h-6" />
            Light
          </button>
          <button
            @click="setTheme('dark')"
            :class="theme === 'dark' ? 'bg-blue-900/20 text-white' : 'text-gray-600'"
            class="flex-1 flex items-center justify-center gap-2 rounded-lg px-3 py-2 text-sm transition-colors"
          >
            <img src="/img/xhAAbgo1ir.png" alt="Moon" class="w-6 h-6" />
            Dark
          </button>
        </div>
      </footer>
    </aside>

    <!-- Mobile Bottom Nav -->
    <nav
      class="fixed md:hidden bottom-0 left-1/2 -translate-x-1/2 !w-full radious-30 bg-white dark:bg-gray-900 border-t border-gray-200 dark:border-gray-700 z-50"
    >
        <div class="absolute left-[40%] bottom-[20%] translate-x-[5%] translate-y-[-3%]">
            <img src="/img/FAB.png" alt="">
        </div>
      <div class="flex justify-around py-2">
        <button
          v-for="item in navItems"
          :key="item.name"
          @click="activeTab = item.name"
          class="flex flex-col items-center py-2 px-4 min-w-0 flex-1 transition-colors"
          :class="activeTab === item.name ? 'text-blue-600 dark:text-blue-400' : 'text-gray-600 dark:text-gray-400'"
        >
          <component :is="item.icon" class="w-6 h-6 mb-1" />
          <span class="text-xs font-medium"><img :src="item.img" alt=""></span> <br>
          <span class="text-xs font-medium">{{ item.name }}</span>
        </button>
      </div>
    </nav>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import NavItem from "./NavItem.vue";

const theme = ref("light");
const activeTab = ref("Referral");

// theme toggle
const setTheme = (mode) => {
  theme.value = mode;
  if (mode === "dark") {
    document.documentElement.classList.add("dark");
  } else {
    document.documentElement.classList.remove("dark");
  }
  localStorage.setItem("theme", mode);
};

onMounted(() => {
  const savedTheme = localStorage.getItem("theme") || "light";
  setTheme(savedTheme);
});

const navItems = [
  {
    name: "Home",
    icon: {
      template: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/></svg>`,
    },
    img: "/img/home.png",
  },
  {
    name: "Payment",
    icon: {
      template: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M20 4H4c-1.11 0-1.99.89-1.99 2L2 18c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V6c0-1.11-.89-2-2-2zm0 14H4v-6h16v6zm0-10H4V6h16v2z"/></svg>`,
    },
    img: "/img/payment.png",
  },
  {
    name: "Referral",
    icon: {
      template: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92s2.92-1.31 2.92-2.92S19.61 16.08 18 16.08z"/></svg>`,
    },
    img: "/img/referal.png",
  },
  {
    name: "Profile",
    icon: {
      template: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg>`,
    },
    img: "/img/profile.png",
  },
];
</script>

<style>
html {
  transition: background-color 0.3s, color 0.3s;
}

.radious-30 {
  border-radius: 30px 30px 0 0 !important;
}
</style>
