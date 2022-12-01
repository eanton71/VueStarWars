<script setup>
import { ref, onMounted } from 'vue';
import Card from './components/Card.vue'
import Loader from './components/Loader.vue'
import Film from './components/Film.vue'
 
const films = ref([])
const addToFilms = (i, tit, int, dir, any, per, pla, nav, veh, esp) => {
  const film = {
    id: i,
    titulo: tit,
    intro: int,
    director: dir,
    anyo: any,
    personajes: per,
    planetas: pla,
    naves: nav,
    vehiculos: veh,
    especies: esp,
    img: 'https://starwars-visualguide.com/assets/img/films/' + i + '.jpg',

  }
  films.value.push(film);
}
const filmCard = ref({})
const loading = ref(true)
const showfilms = ref(false)
const showcard = ref(false)
const boton_inicio = ref(false)
const API_STAR_WARS = 'https://swapi.dev/api/films/'
fetch(API_STAR_WARS)
  .then(response => response.json())
  .then(data => {
    films.total = data.count;

    for (let i = 0; i < films.total; i++) { 
      let id = data.results[i].url.slice(28, 29);
      let tit = data.results[i].title;
      let int = data.results[i].opening_crawl;
      let dir = data.results[i].director;
      let any = data.results[i].release_date.slice(0, 4);
      let per = data.results[i].characters.length;
      let pla = data.results[i].planets.length;
      let nav = data.results[i].starships.length;
      let veh = data.results[i].vehicles.length;
      let esp = data.results[i].species.length;
      addToFilms(id, tit, int, dir, any, per, pla, nav, veh, esp);

    }


  })
  .catch(error => {
    console.error(error);
  });

const inicio = () => {
  showcard.value = false
  showfilms.value = true
  boton_inicio.value = false
}
const showFilm = (ev) => { 
  filmCard.value = films.value.find(film => film.id === ev.target.id) 
  showcard.value = true
  showfilms.value = false
  boton_inicio.value = true
}
onMounted(() => {
  setTimeout(() => {
    loading.value = false
    showfilms.value = true 
  }, 2000);
   
})  
</script>

<template>
  <header>
    <h1>Star Wars</h1>
    <nav>
      <button v-if="boton_inicio" @click="inicio" id="inicio" class="inicio">Inicio</button>
    </nav>
  </header>
  <main>

    <template v-if="loading">
      <Loader>
      </Loader>
    </template>

    <template v-if="showfilms">
      <div class="films">
        <Film 
        v-for="film in films" 
        :id="film.id"
        :titulo="film.titulo" 
        :img="film.img" 
        @click="showFilm"
        />
      </div>
    </template>
    <template v-if="showcard">
      <Card
      :img="filmCard.img"
      :titulo="filmCard.titulo"
      :intro="filmCard.intro"
      :director="filmCard.director"
      :anyo="filmCard.anyo"
      :personajes="filmCard.personajes"
      :planetas="filmCard.planetas"
      :naves="filmCard.naves"
      :vehiculos="filmCard.vehiculos"
      :especies="filmCard.especies"
      />
    </template>

  </main>
</template>

<style scoped>
.films {
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
</style>
