<script setup>
const sections = ['Finance', 'Sales', 'HR', 'MGMT']
const date = Date.now()
</script>

<template>
  <header class="px-4 pt-4 pb-2 sm:px-6 lg:px-10">
    <div class="flex items-center justify-between">
      <div>
        <p class="text-sm font-semibold text-slate-800">The Essentials.</p>
        <p class="text-xs text-slate-500">Here’s how your business is performing today.</p>
      </div>


      <div class="flex gap-5">
        <img src="/menu.png" alt="Logo" class=" object-cover w-10 h-10 rounded-full " />
          <nav class=" bg-white rounded-full w-[400px]">
            <a href="/">FINANCE</a>
            <a href="/">SALES</a>
            <a href="/">HR</a>
            <a href="/">MGMT</a>
          </nav>
      </div> 

      <div>
        {{date}}
        </div>
      <div>
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
  </header>
</template>

