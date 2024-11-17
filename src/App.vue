<script setup>
import { ref } from 'vue';
import FormularioCita from './components/FormularioCita.vue';
import CitaPaciente from './components/CitaPaciente.vue';

const pacientes = ref([]);
const addPaciente = (nuenvoPaciente) => {
  pacientes.value.push(nuenvoPaciente);
}

const deletePaciente = (idPaciente) => {
  pacientes.value.splice(idPaciente, 1);
}
</script>

<template>
  <h1 class="text-center mt-3">Consultas Medicas</h1>
  <FormularioCita @agregar-citas="addPaciente" />
  <div v-show="pacientes.length == 0">
    <p :style="{ color: 'red', textAlign: 'center' }">No hay consultas registradas</p>
  </div>
  <div class="pacientes">
    <CitaPaciente v-for="(paciente, index) in pacientes" :key="index" :paciente="paciente.paciente"
      :fecha="paciente.fecha" :hora="paciente.hora" :gravedad="paciente.gravedad" :motivo="paciente.motivo"
      :idPaciente="index" @eliminarCita="deletePaciente(index)" />
  </div>
</template>
<style scoped>
.pacientes {
  margin-top: 2.5rem;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>