<script setup>
import { useSlots, computed } from 'vue';

const slots = useSlots();

// Contamos cuántos elementos (nodos) hay en el slot del header
const columnCount = computed(() => {
  if (slots.header) {
    // Filtramos para contar solo elementos reales y no espacios en blanco
    return slots.header().filter(node => node.type !== Symbol.for('v-txt')).length;
  }
  return 4; // Valor por defecto si no hay header
});

// Generamos la clase de grid dinámica
const gridStyle = computed(() => {
  return {
    gridTemplateColumns: `repeat(${columnCount.value}, minmax(0, 1fr))`
  };
});
</script>

<template>
  <div class="w-full border border-gray-200 rounded-xl overflow-hidden shadow-sm bg-white mb-6">
    <div 
      :style="gridStyle"
      class="grid gap-4 bg-gray-50 p-4 font-bold text-gray-500 text-xs uppercase tracking-wider border-b border-gray-200"
    >
      <slot name="header"></slot>
    </div>

    <div class="divide-y divide-gray-100">
      <slot :gridStyle="gridStyle"></slot>
    </div>
  </div>
</template>
