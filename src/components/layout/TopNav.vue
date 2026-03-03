<script setup>
const sections = ['Finance', 'Sales', 'HR', 'MGMT']
</script>

<template>
  <header class="px-4 pt-4 pb-2 sm:px-6 lg:px-10">
    <div class="flex items-center justify-between gap-4 max-w-6xl ">
      <div class="space-y-1">
        <p class="text-sm font-semibold text-slate-800">The Essentials.</p>
        <p class="text-xs text-slate-500">Here’s how your business is performing today.</p>
      </div>

      <div
        class="flex flex-1 items-center justify-center gap-3 max-w-xl mx-4 rounded-full bg-white/70 shadow-card px-2 py-1 text-xs font-medium"
      >
        <nav class="inline-flex items-center rounded-full bg-surface-muted px-1 py-1">
          <button
            v-for="section in sections"
            :key="section"
            type="button"
            class="px-3 py-1 rounded-full transition-colors"
            :class="
              section === 'Finance'
                ? 'bg-primary text-white shadow-sm'
                : 'text-slate-500 hover:text-slate-900'
            "
          >
            {{ section.toUpperCase() }}
          </button>
        </nav>

        <div class="hidden md:flex items-center gap-3">
          <button
            type="button"
            class="inline-flex items-center gap-2 text-xs text-slate-500 bg-surface-muted rounded-full px-3 py-1"
          >
            <span>Sep 25</span>
          </button>

          <!-- Desktop pill with quick actions -->
          <div class="hidden lg:flex items-center gap-3">
            <button
              type="button"
              class="inline-flex items-center justify-center w-9 h-9 rounded-full bg-surface-muted text-slate-500"
            >
              ☰
            </button>

            <div
              class="inline-flex items-center gap-2 bg-primary rounded-full px-3 py-1 text-xs text-white shadow-card"
            >
              <span class="w-7 h-7 rounded-full bg-white/12 flex items-center justify-center text-[10px]">
                ☁
              </span>
              <span class="w-7 h-7 rounded-full bg-white/12 flex items-center justify-center text-[10px]">
                ✦
              </span>
              <span class="w-7 h-7 rounded-full bg-white/12 flex items-center justify-center text-[10px]">
                ⚙
              </span>
              <span class="w-7 h-7 rounded-full bg-white/12 flex items-center justify-center text-[10px]">
                🔥
              </span>
            </div>
          </div>
        </div>

        <!-- Compact right cluster for small screens -->
        <button
          type="button"
          class="md:hidden inline-flex items-center justify-center w-9 h-9 rounded-full bg-primary text-white shadow-card"
        >
          ☰
        </button>
      </div>
    </div>
  </header>
</template>

