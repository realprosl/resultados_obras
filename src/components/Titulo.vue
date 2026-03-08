<script setup>
defineProps({
  id: {
    type: String,
    default: 'PROY-000'
  },
  name: {
    type: String,
    default: 'Nombre del Proyecto'
  }
});
</script>

<template>
  <div class="flex flex-col md:flex-row md:items-center gap-4 mb-8 pb-6 border-b border-gray-200">
    <div class="flex items-center gap-2">
      <div class="bg-slate-900 text-slate-100 px-3 py-1 rounded-lg font-mono text-sm font-bold shadow-sm">
        {{ id }}
      </div>
    </div>

    <div class="hidden md:block h-8 w-px bg-gray-300 mx-2"></div>

    <div class="flex flex-col">
      <h1 class="text-2xl font-extrabold text-slate-800 leading-tight">
        {{ name }}
      </h1>
    </div>
  </div>
</template>
