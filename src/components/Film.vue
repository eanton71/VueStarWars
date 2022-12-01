<template>
    <div  class="film">
         
        <img :id="id" :src="img" @click="showFilm">
        <h3> Titulo:  {{ titulo }}</h3>
    </div>
</template>

<script setup>
import { ref, watch } from 'vue'
const emit = defineEmits(['idShow'])
const show = ref(false)

watch(show, () => {
    emit('idShow', props.id);
})
const props = defineProps({
    id: {
        type: String,
        default: "",
        required: true
    },
    titulo: {
        type: String,
        default: "",
        required: true
    },
    img: {
        type: String,
        default: "",
        required:true
    }
})
const showFilm = () => {
    show.value=true
}
</script>

<style scoped>
.film {
     background-color: dimgray;
     border: 1px solid black;
     color: aquamarine;
     width: 200px;
     height: 300px;
     margin: 1% 5%;
     text-align: center;
 }

 .film:hover {
     background-color: gray;
     border: 1px dotted red; 
 }

 .film:hover h3 {
     color: chartreuse;
 }

 .film>img {
     /*width: 90%;*/
     aspect-ratio: 1;
     object-fit: cover;
     width: 90%;
     height: 70%;
 }
</style>