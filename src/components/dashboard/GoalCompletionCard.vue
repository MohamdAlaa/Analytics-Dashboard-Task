<script setup>
import { computed } from 'vue'
import Chart from 'primevue/chart'

const completion = 0.72

const data = computed(() => ({
  labels: ['Completed', 'Remaining'],
  datasets: [
    {
      data: [completion * 100, (1 - completion) * 100],
      backgroundColor: ['#2F7BF6', '#E5EDFF'],
      borderWidth: 0
    }
  ]
}))

const options = computed(() => ({
  cutout: '70%',
  plugins: {
    legend: {
      display: false
    },
    tooltip: {
      enabled: false
    }
  }
}))
</script>

<template>
  <section class="bg-surface shadow-card rounded-card px-5 py-4 flex items-center gap-4">
    <div class="w-24 h-24">
      <Chart type="doughnut" :data="data" :options="options" />
    </div>
    <div class="space-y-1">
      <p class=" uppercase tracking-wide text-green-500 text-base">Goal Completion</p>
      <p class="text-xl font-semibold text-slate-900">{{ Math.round(completion * 100) }}%</p>
      <p class=" text-slate-400">Quarterly revenue target reached.</p>
    </div>
  </section>
</template>

