<script setup>
import { computed } from 'vue'
import KpiCard from './KpiCard.vue'
import ChartCard from './ChartCard.vue'
import ScenarioPanel from './ScenarioPanel.vue'
import MiniLineCard from './MiniLineCard.vue'
import GoalCompletionCard from './GoalCompletionCard.vue'
import { Slider } from 'primevue'

const kpis = [
  {
    label: 'Revenue',
    value: '1,400,000',
    subtitle: 'vs previous month',
    trend: '+12.4%'
  },
  {
    label: 'Gross Profit',
    value: '1,250,000',
    subtitle: 'vs previous month',
    trend: '+8.1%'
  },
  {
    label: 'Op. Expenses',
    value: '600,000',
    subtitle: 'vs previous month',
    trend: '-3.2%'
  },
  {
    label: 'Net Income',
    value: '650,000',
    subtitle: 'vs previous month',
    trend: '+5.0%'
  },
  {
    label: 'Cash in Bank',
    value: '1,700,000',
    subtitle: 'vs previous month',
    trend: '+2.5%'
  },
  {
    label: 'Burn Rate',
    value: '410,000',
    subtitle: 'vs previous month',
    trend: '-1.2%'
  },
  {
    label: 'Runway',
    value: '4.1 → 6.5',
    subtitle: 'months',
    trend: '+2.4'
  }
]

const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']

const revenueVsExpensesData = computed(() => ({
  labels: months,
  datasets: [
    {
      label: 'Revenue',
      backgroundColor: '#2F7BF6',
      borderRadius: 999,
      data: [650, 720, 690, 730, 760, 780, 800, 820, 780, 760, 740, 720]
    },
    {
      label: 'Expenses',
      backgroundColor: '#F76AA6',
      borderRadius: 999,
      data: [540, 580, 560, 590, 620, 640, 660, 670, 650, 630, 610, 600]
    }
  ]
}))

const cashInflowOutflowData = computed(() => ({
  labels: months,
  datasets: [
    {
      label: 'Inflow',
      fill: true,
      borderColor: '#2F7BF6',
      backgroundColor: 'rgba(47, 123, 246, 0.22)',
      tension: 0.4,
      data: [500, 560, 540, 580, 620, 640, 650, 660, 640, 620, 610, 600]
    },
    {
      label: 'Outflow',
      fill: true,
      borderColor: '#F76AA6',
      backgroundColor: 'rgba(247, 106, 166, 0.18)',
      tension: 0.4,
      data: [420, 450, 440, 470, 500, 520, 530, 540, 520, 510, 500, 490]
    }
  ]
}))

const cashInBankData = computed(() => ({
  labels: months.slice(0, 6),
  datasets: [
    {
      label: 'Cash in Bank',
      borderColor: '#2F7BF6',
      backgroundColor: 'rgba(47, 123, 246, 0.16)',
      fill: true,
      tension: 0.4,
      data: [1.1, 1.2, 1.25, 1.3, 1.35, 1.4]
    }
  ]
}))

const netFlowData = computed(() => ({
  labels: months.slice(0, 6),
  datasets: [
    {
      label: 'Net Flow',
      borderColor: '#F76AA6',
      backgroundColor: 'rgba(247, 106, 166, 0.16)',
      fill: true,
      tension: 0.4,
      data: [0.18, 0.22, 0.2, 0.24, 0.26, 0.25]
    }
  ]
}))

const scenarioRows = [
  { label: 'Inflow', current: '$1,700,000', adjusted: '$1,950,000', change: '+14.7%' },
  { label: 'Outflow', current: '$650,000', adjusted: '$710,000', change: '+9.2%' },
  { label: 'Net Cash Flow', current: '4.1', adjusted: '6.5', change: '+2.4' }, 
  { label: 'Cash Balance', current: '58%', adjusted: '58%', change: '+2.4' }
]

const profitLossData = computed(() => ({
  labels: months.slice(0, 8),
  datasets: [
    {
      label: 'Profit / Loss',
      borderColor: '#F76AA6',
      backgroundColor: 'rgba(247, 106, 166, 0.16)',
      fill: true,
      tension: 0.4,
      data: [120, 160, 140, 130, 170, 190, 210, 200]
    }
  ]
}))
</script>

<template>
  <div class="space-y-5 lg:space-y-6">
    <!-- KPI row -->
    <div class="grid gap-3 sm:gap-4 md:grid-cols-3 xl:grid-cols-7">
      <KpiCard
        v-for="kpi in kpis"
        :key="kpi.label"
        :label="kpi.label"
        :value="kpi.value"
        :subtitle="kpi.subtitle"
        :trend="kpi.trend"
      />
    </div>

    <!-- Top band: bar chart + mini charts + tuner -->
    <div
      class="grid gap-5 lg:gap-6 xl:grid-cols-[minmax(0,2.3fr)_minmax(0,1.2fr)_minmax(0,1.5fr)]"
    >
      <!-- Left: main bar chart -->
      <ChartCard
        title="Revenue vs Expenses"
        subtitle="Losses in March and April driven by seasonality + marketing spikes."
        type="bar"
        :data="revenueVsExpensesData"
      />

      <!-- Middle: profit/loss + goal completion -->
      <div class="space-y-5 lg:space-y-6">
        <MiniLineCard
          title="Profit / Loss"
          label="+12.4% vs last month"
          value="$210,000"
          :data="profitLossData"
        />
        <GoalCompletionCard />
      </div>

      <!-- Right: Forecast & Budget Tuner -->
      <div class="space-y-5 lg:space-y-6">
        <ScenarioPanel
          title="Forecast & Budget Tuner"
          description="Adjust revenue, OPEX, and COGS assumptions to see profit scenarios live."
          :sliders="['Revenue Growth', 'COGS % of Revenue', 'CapEx Change', 'Seasonality', 'Pipeline Confidence']"
        />
      </div>
    </div>

    <!-- Middle row: cash inflow vs outflow + Cash Flow Scenario Tuner -->
    <div class="grid gap-5 lg:gap-6 lg:grid-cols-[minmax(0,2.1fr)_minmax(0,1.4fr)]">
      <ChartCard
        title="Cash inflow vs outflow"
        type="line"
        :data="cashInflowOutflowData"
        :options="{
          plugins: { legend: { position: 'top' } }
        }"
      />

      <section class="bg-surface shadow-card rounded-card p-5 sm:p-6 space-y-4">
        <header class="space-y-1">
          <p class=" font-extrabold text-slate-900">Cash Flow Scenario Tuner</p>
          <p class=" font-semibold text-slate-500">
            Adjust inflow, outflow, and operational levers to see instant impact on runway and cash
            position.
          </p>
        </header>

        <div class="flex justify-between text-base font-medium">
          <div class="flex flex-col gap-5">
            <span>Inflow Sensitivity</span>
            <Slider v-model="value"  class="w-36 " />
          </div>
          <div class="flex flex-col gap-5">
            <span>OpEx Tightening</span>
            <Slider v-model="value"  class="w-36 " />
          </div>
          <div class="flex flex-col gap-5">
            <span>Payment Terms</span>
            <Slider v-model="value"  class="w-36 " />
          </div>
        </div>

        <div class="bg-primary text-white rounded-b-3xl p-3 text-[11px] space-y-2">
          <div class="grid grid-cols-4 gap-2 font-medium text-base">
            <span>Output Snapshot</span>
            <span>Current</span>
            <span>Adjusted</span>
            <span>Changes</span>
          </div>
          <div
            v-for="row in scenarioRows"
            :key="row.label"
            class="grid grid-cols-4 gap-2 items-center border-t border-white/15 pt-1.5 mt-1.5"
          >
            <span class="text-base text-slate-900 font-medium">{{ row.label }}</span>
            <span class=" text-base text-slate-900 font-medium">{{ row.current }}</span>
            <span class="text-base text-slate-900 font-medium">{{ row.adjusted }}</span>
            <span class="text-base  font-medium">{{ row.change }}</span>
          </div>
        </div>

        <p class="text-[11px] text-slate-500 leading-relaxed">
          “Adjusting inflow, outflow, and payment timing helps you see how cash balance may shift.
          Higher inflow or tighter spending usually support a stronger cash position.”
        </p>
      </section>
    </div>

    <!-- Bottom small charts row -->
    <div class="grid gap-5 lg:gap-6 lg:grid-cols-[minmax(0,2fr)_minmax(0,1.2fr)]">
      <ChartCard title="Cash in Bank" type="line" :data="cashInBankData" />

      <ChartCard title="Net Flow" type="line" :data="netFlowData" />
    </div>
  </div>
</template>

