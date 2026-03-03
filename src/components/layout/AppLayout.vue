<script setup>
import TopNav from './TopNav.vue'
import Navbar from './Navbar.vue'
import SidebarNav from './SidebarNav.vue'
import MainDashboard from '../dashboard/MainDashboard.vue'
</script>

<template>
  <div class="min-h-screen flex bg-white">
    <!-- Sidebar -->
    <aside
      class="hidden lg:flex flex-col  py-6 px-4 bg-surface shadow-card rounded-r-card w-20"
    >
      <div class="flex flex-col items-center gap-72">
          <span class="font-semibold text-6xl font-lora text-slate-700 relative">g<span class="font-lora text-blue-500 text-5xl absolute top-[-4px] ">.</span></span>
        <SidebarNav />
      </div>
    </aside>

    <!-- Main content -->
    <div class="flex-1 flex flex-col min-h-screen bg-gray-300 rounded-3xl m-4">
      <Navbar />
      <TopNav />

      <main class="flex-1 px-2 pb-6 pt-3 sm:px-4 lg:px-8 flex justify-center"> <MainDashboard />
      </main>
    </div>
  </div>
</template>

