<script setup>
import { Slider } from 'primevue';

defineProps({
  title: String,
  description: String,
  sliders: {
    type: Array,
    default: () => []
  }
})

const rows = [
  { label: 'Gross Profit', current: '$640,000', adjusted: '$650,000', change: '+1.6%' },
  { label: 'Net Income', current: '$650,000', adjusted: '$670,000', change: '+3.0%' },
  { label: 'Runway (months)', current: '4.1', adjusted: '6.5', change: '+2.4' },
  { label: 'Gross Margin', current: '52%', adjusted: '52%', change: '+2.4' }
]
</script>

<template>
  <section class="bg-surface shadow-card rounded-card p-5 sm:p-6 flex flex-col gap-4">
    <header class="space-y-1 ">
      <p class=" font-extrabold text-slate-900">{{ title }}</p>
      <p class=" text-slate-500 font-semibold">
        {{ description }}
      </p>
    </header>

    <div class="grid grid-cols-3 gap-10 ">
      <div
        v-for="slider in sliders"
        :key="slider"
        class="flex items-center justify-between "
      >
      <div class="flex flex-col gap-4">
        <span class="text-slate-900 font-medium">{{ slider }}</span>
        <Slider v-model="value"  class="w-36 h-36 " />
      </div>
      </div>
    </div>

    <div class="bg-primary text-white rounded-b-3xl p-3 text-[11px] space-y-2">
      <div class="grid grid-cols-4 gap-2 font-medium text-base">
        <span class="">Output Snapshot</span>
        <span>Current</span>
        <span>Adjusted</span>
        <span>Changes</span>
      </div>
      <div
        v-for="row in rows"
        :key="row.label"
        class="grid grid-cols-4 gap-2 items-center border-t border-white/15 pt-1.5 mt-1.5"
      >
        <span class="text-base text-slate-900 font-medium">{{ row.label }}</span>
        <span class=" text-base text-slate-900 font-medium">{{ row.current }}</span>
        <span class=" text-base text-slate-900 font-medium">{{ row.adjusted }}</span>
        <span class="text-base   font-medium">{{ row.change }}</span>
      </div>
    </div>

    <button
      type="button"
      class="mt-1 inline-flex items-center justify-center rounded-full bg-primary text-white   font-medium py-2 px-4 self-start shadow-card"
    >
      Generate
    </button>
  </section>
</template>

