<script setup>
defineProps(['items']);
defineEmits(['remove']);
</script>

<template>
  <div v-for="item in items" :key="item.id" :style="$parent.gridStyle" 
       class="group grid gap-4 p-4 hover:bg-slate-50 items-center transition-all relative">
    
    <input v-model="item.nombre" placeholder="Material..." class="bg-transparent border-b border-transparent focus:border-green-500 outline-none p-1 w-full text-sm">
    
    <div class="flex items-center gap-1">
      <input v-model.number="item.cantidad" type="number" class="bg-transparent border-b border-transparent focus:border-green-500 outline-none p-1 w-full text-center text-sm">
      <input v-model.number="item.unidad" class="text-[10px] text-gray-400 font-bold uppercase">
    </div>

    <input v-model.number="item.costo" type="number" class="bg-transparent border-b border-transparent focus:border-green-500 outline-none p-1 w-full text-center text-sm">

    <div class="relative flex justify-center items-center h-full">
      <span class="font-bold text-green-600 transition-opacity duration-200 group-hover:opacity-0 text-sm">
        ${{ (item.cantidad * item.costo).toLocaleString() }}
      </span>
      <button @click="$emit('remove', item.id)" class="absolute opacity-0 group-hover:opacity-100 transition-all duration-200 bg-red-50 text-red-600 px-3 py-1 rounded-md border border-red-200 hover:bg-red-600 hover:text-white flex items-center gap-1 text-[10px] font-bold">
        <span>X</span>
      </button>
    </div>
  </div>
</template>
