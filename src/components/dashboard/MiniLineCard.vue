<script setup>
import { computed } from 'vue'
import Chart from 'primevue/chart'

const props = defineProps({
  title: String,
  label: String,
  value: String,
  data: {
    type: Object,
    required: true
  }
})

const options = computed(() => ({
  maintainAspectRatio: false,
  plugins: {
    legend: {
      display: false
    },
    tooltip: {
      mode: 'index',
      intersect: false
    }
  },
  scales: {
    x: {
      display: false
    },
    y: {
      display: false
    }
  }
}))
</script>

<template>
  <section class="bg-surface shadow-card rounded-card px-5 py-4 flex flex-col gap-3">
    <header class="flex items-center justify-between gap-2">
      <div>
        <p class="text-xs uppercase tracking-wide text-slate-400">{{ title }}</p>
        <p class="text-sm font-semibold text-slate-900">{{ value }}</p>
      </div>
      <p class="text-[11px] text-emerald-500 font-medium">{{ label }}</p>
    </header>

    <div class="h-56">
      <Chart type="line" :data="data" :options="options" />
    </div>
  </section>
</template>

