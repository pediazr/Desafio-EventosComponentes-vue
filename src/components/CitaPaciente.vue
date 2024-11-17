<script setup>

const props = defineProps({
    paciente: String,
    fecha: String,
    hora: String,
    gravedad: String,
    motivo: String,
    idPaciente: Number
});

const emit = defineEmits(['eliminarCita']);
const deleteCita = () => {
    emit('eliminarCita');//,props.idPaciente
}
</script>

<template>
    <div class="card" :class="gravedad === 'Baja' ? 'green' : gravedad === 'Media' ? 'yellow' : 'red'">
        <h3>Cita</h3>
        <label><b>Paciente</b></label>
        <label>{{ props.paciente }}</label>
        <label><b>Fecha</b></label>
        <label>{{ props.fecha }}</label>
        <label><b>Hora</b></label>
        <label>{{ props.hora }}</label>
        <label><b>Motivo</b></label>
        <label>{{ props.motivo }}</label>
        <button class="mt-3" @click="deleteCita">Eliminar</button>


    </div>
</template>

<style scoped>
.card {
    min-width: 10rem;
    padding: 1rem;
    border-radius: 0.5rem;
    text-align: center;
}

.yellow {
    background-color: #f7f781;
}

.green {
    background-color: #8ce28c;
}

.red {
    background-color: #ee7d7d;
}
</style>