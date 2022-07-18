<template>
  <div>
    <AddFilm @add:film="addFilm" />
    <FilmListe :films="films" @deleteAll="deleteAllFilms" @deleteFilm:film="deleteFilm" @update:film="updateFilm"/>
  </div>
</template>

<script>
import AddFilm from "./components/AddFilm.vue";
import FilmListe from "./components/FilmListe.vue";
export default {
  name: "App",
  components: {
    AddFilm,
    FilmListe,
  },
  data() {
    return {
      films: [],
    };
  },
  methods: {
    addFilm(film) {
      const newFilm = {
        yonetmen: film.yonetmen,
        link: film.link,
        filmName: film.filmName,
        id:this.films.length+1
      };
      
      console.log(newFilm.id)
      this.films.push(newFilm);
    },
    deleteAllFilms() {
      this.films.length=0
    },
    deleteFilm(film){
      for(let i=0;i<this.films.length;i++){
        if(this.films[i]===film){
          this.films.splice(i,1)
        }
      }
    },
    updateFilm(film){
      for(let i=0;i<this.films.length;i++){
        if(this.films[i]===film){
          this.films.link=film.link;
          this.films.filmName=film.filmName;
          this.films.yonetmen=film.yonetmen;
        }
      }
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
