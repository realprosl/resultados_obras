<script setup>
import { ref } from 'vue';
import Title from './components/Titulo.vue';
import PseudoTabla from './components/Table.vue';
import TablaManoObra from './components/ManoObra.vue';
import TablaMateriales from './components/Materiales.vue';

// Datos Reactivos

const Obra = ref({
  name: "Calle La Ostia n2",
  id: "2025",
  manoObra :[
    { id: new Date().toISOString().split('T')[0], trabajador: 'Juan Pérez', rol: 'Pintor', dias: 8, precio: 20 }
  ],
  materiales:[],
});

// Funciones de acción
const agregarManoObra = () => {
  Obra.value.manoObra.push({
    id: new Date().toISOString().split('T')[0],
    trabajador: '',
    rol: '',
    dias: 0,
    precio: 20
  });
};

const eliminarManoObra = (id) => {
  Obra.value.manoObra = Obra.value.manoObra.filter(item => item.id !== id);
};

const agregarMaterial = () => {
  Obra.value.materiales.push({
    id: Date.now(),
    nombre: '',
    cantidad: 0,
    unidad: 'und',
    costo: 0
  });
};

const eliminarMaterial = (id) => {
  Obra.value.materiales = Obra.value.materiales.filter(item => item.id !== id);
};
</script>

<template>
  <div class="p-8 max-w-5xl mx-auto">

    <Title :id="Obra.id" :name="Obra.name"/>
    
    <section>
      <div class="flex justify-between items-center mb-4">
        <h2 class="text-xl font-bold text-blue-700">Mano de Obra</h2>
        <button @click="agregarManoObra" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition font-medium">
          +
        </button>
      </div>
      <PseudoTabla>
        <template #header>
          <div>Fecha</div>
          <div>Nombre</div>
          <div>Cargo/Rol</div>
          <div class="text-center">Dias</div>
          <div class="text-center">Precio</div>
          <div class="text-center">Subtotal</div>
        </template>
        <TablaManoObra :items="Obra.manoObra" @remove="eliminarManoObra" />
      </PseudoTabla>
    </section>

    <section>
      <div class="flex justify-between items-center mb-4">
        <h2 class="text-xl font-bold text-green-700">Materiales</h2>
        <button @click="agregarMaterial" class="bg-green-600 text-white px-4 py-2 rounded-lg hover:bg-green-700 transition font-medium">
          +
        </button>
      </div>
      <PseudoTabla>
        <template #header>
          <div>Descripción</div>
          <div class="text-center">Cantidad</div>
          <div class="text-center">Precio Unit.</div>
          <div class="text-center">Subtotal</div>
        </template>
        <TablaMateriales :items="Obra.materiales" @remove="eliminarMaterial" />
      </PseudoTabla>
    </section>

  </div>
</template>
