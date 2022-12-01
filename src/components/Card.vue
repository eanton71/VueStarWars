<template>
    <div id="card" class="card">
        <img :src="img" />
        <table>
            <tr > 
                <td colspan="2"><h2>{{ titulo }}</h2></td>
            </tr>
            <tr class="intro">
                <td colspan="2">{{ intro }}</td> 
            </tr>
             
            <tr v-for="(value, key) in vars"> 
                <td><b>{{ key }}:  </b></td>
                <td>{{value}}</td>
            </tr> 
            
        </table>
    </div>
</template>

<script setup>
import { reactive } from 'vue'
const vars = reactive({
    "Director": props.director,
    "Año": props.anyo,
    "Nº personajes": props.personajes,
    "Nº planetas": props.planetas,
    "Nº naves": props.naves,
    "Nº vehiculos": props.vehiculos,
    "Nº especies": props.especies
})
const props = defineProps({
 
    img: {
        type: String,
        default: "",
        required: true
    },
    titulo: {
        type: String,
        default: "",
        required: true
    },
    director: {
        type: String,
        default: "",
        required: true
    },
    intro: {
        type: String,
        default: "",
        required: true
    },
    anyo: {
        type: String,
        default: "",
        required: true
    },
    personajes: {
        type: String,
        default: "",
        required: true
    },
    planetas: {
        type: String,
        default: "",
        required: true
    },
    naves: {
        type: String,
        default: "",
        required: true
    },
    vehiculos: {
        type: String,
        default: "",
        required: true
    },
    especies: {
        type: String,
        default: "",
        required: true
    }

})
</script>

<style scoped>
.card {
    background-color: black;
    border: 1px solid rgb(134, 96, 96);
    margin: 0% auto 2% auto;
    width: 94%;
    height: 80%;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-flow: row wrap;

}

.card img {
    width: 40%;
    min-width: 200px;
    min-height: 300px;
    height: 80%;
    position: relative;
}

.card table {
    width: 50%;
    min-width: 200px;
    height: 80%;
    min-height: 300px;
    position: relative;
    background-color: rgb(44, 23, 23);
    color: aquamarine;
    padding: 2px;
    text-align: center;
}



th,
td {
    padding: 10px;
    border: 1px solid gray;
    background-color: rgb(87, 23, 23);
}
.intro{
overflow: auto;
}
</style>