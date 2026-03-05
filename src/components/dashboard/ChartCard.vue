<script setup>
import { computed } from 'vue'
import Chart from 'primevue/chart'

const props = defineProps({
  title: String,
  subtitle: String,
  type: {
    type: String,
    default: 'bar'
  },
  data: {
    type: Object,
    required: true
  },
  options: {
    type: Object,
    default: () => ({})
  }
})

const chartOptions = computed(() => ({
  maintainAspectRatio: false,
  plugins: {
    legend: {
      display: false,
      position: 'bottom',
      labels: {
        boxWidth: 8,
        boxHeight: 8,
        usePointStyle: true
      }
    },
    tooltip: {
      mode: 'index',
      intersect: false
    }
  },
  scales: {
    x: {
      grid: {
        display: false
      }
    },
    y: {
      grid: {
        color: '#E2E8F0'
      }
    }
  },
  ...props.options
}))
</script>

<template>
  <section class="bg-surface rounded-card p-4 sm:p-5 flex flex-col gap-3">
    <header class="flex items-center justify-between gap-2">
      <div>
        <p class="text-sm font-semibold text-slate-900">{{ title }}</p>
        <p v-if="subtitle" class="text-xs text-slate-400">{{ subtitle }}</p>
      </div>
    </header>

    <div class="h-56 sm:h-64 lg:h-full">
      <Chart :type="type" :data="data" :options="chartOptions" class="h-full" />
    </div>
  </section>
</template>

