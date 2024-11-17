<script setup>
import { ref } from 'vue';
const paciente = ref("");
const hora = ref("");
const fecha = ref("");
const gravedad = ref("");
const motivo = ref("");
const tipoGravedad = ["Baja", "Media", "Alta"];

const emit = defineEmits(['agregarCitas']);
const addCita = () => {
    emit('agregarCitas', {
        paciente: paciente.value,
        fecha: fecha.value,
        hora: hora.value,
        gravedad: gravedad.value,
        motivo: motivo.value
    });
    paciente.value = "";
    hora.value = "";
    fecha.value = "";
    gravedad.value = "";
    motivo.value = "";
}

const validForm = () => {
    return paciente.value && hora.value && fecha.value && gravedad.value && motivo.value;
}

</script>

<template>
    <form @submit.prevent="addCita" class="container mt-5 border rounded p-5">
        <div class="row fw-bold ">
            <div class="col">
                <div class="col text-center text-danger">
                    <label for="paciente" :style="{ color: paciente === '' ? 'red' : 'black' }">Paciente</label>
                </div>
                <div class="col text-center">
                    <input type="text" id="paciente" v-model="paciente" />
                </div>
            </div>
            <div class="col">
                <div class="col text-center text-danger">
                    <label for="fecha" :style="{ color: fecha === '' ? 'red' : 'black' }">Fecha</label>
                </div>
                <div class="col text-center">
                    <input type="date" id="fecha" v-model="fecha" />
                </div>
            </div>
            <div class="col">
                <div class="col text-center text-danger">
                    <label for="hora" :style="{ color: hora === '' ? 'red' : 'black' }">Hora</label>
                </div>
                <div class="col text-center">
                    <input type="time" id="hora" v-model="hora" />
                </div>
            </div>
            <div class="col">
                <div class="col text-center text-danger">
                    <label for="gravedad" :style="{ color: gravedad === '' ? 'red' : 'black' }">Gravedad</label>
                </div>
                <div class="col text-center">
                    <select id="gravedad" v-model="gravedad">
                        <option v-for="(tipo, id) in tipoGravedad" :key="id">{{ tipo }}</option>
                    </select>
                </div>
            </div>
            <div class="col">
                <div class="col text-center text-danger">
                    <label for="motivo" :style="{ color: motivo === '' ? 'red' : 'black' }">Motivo</label>
                </div>
                <div class="col text-center">
                    <input type="text" v-model="motivo">
                </div>
            </div>
        </div>
        <div class="text-center mt-5">
            <button class="btn btn-info" type="submit" :disabled="!validForm()">Agregar</button>
        </div>
    </form>
</template>

<style scoped></style>