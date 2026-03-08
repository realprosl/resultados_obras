<script setup>
defineProps(['items']);
defineEmits(['remove']);
</script>

<template>
  <div v-for="item in items" :key="item.id" :style="$parent.gridStyle"
       class="group grid gap-6 p-6 hover:bg-slate-50 items-center transition-all relative">
    
    <input v-model.date="item.id" type="date" class="bg-transparent border-b border-transparent focus:border-blue-500 outline-none p-1 w-full text-center text-sm">
    <input v-model="item.trabajador" placeholder="Nombre..." class="bg-transparent border-b border-transparent focus:border-blue-500 outline-none p-1 w-full text-sm">
    <input v-model="item.rol" placeholder="Rol..." class="bg-transparent border-b border-transparent focus:border-blue-500 outline-none p-1 w-full text-gray-500 text-sm">
    <input v-model.number="item.dias" type="number" class="bg-transparent border-b border-transparent focus:border-blue-500 outline-none p-1 w-full text-center text-sm">
    <input v-model.number="item.precio" type="number" class="bg-transparent border-b border-transparent focus:border-blue-500 outline-none p-1 w-full text-center text-sm">

    <div class="relative flex justify-center items-center h-full">
      <span class="font-bold text-blue-600 transition-opacity duration-200 group-hover:opacity-0 text-sm">
        ${{ (item.dias * item.precio).toLocaleString() }}
      </span>
      <button @click="$emit('remove', item.id)" class="absolute opacity-0 group-hover:opacity-100 transition-all duration-200 bg-red-50 text-red-600 px-3 py-1 rounded-md border border-red-200 hover:bg-red-600 hover:text-white flex items-center gap-1 text-[10px] font-bold">
        <span>X</span>
      </button>
    </div>
  </div>
</template>
