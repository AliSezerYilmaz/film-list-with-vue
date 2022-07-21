<template>
  <div>
    <AddFilm @add:film="addFilm" />
    <FilmListe
      :films="films"
      @deleteAll="deleteAllFilms"
      @deleteFilm:film="deleteFilm"
      @update:film="updateFilm"
      @deleteUpdateFilm:film="deleteUpdate"
    />
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
      
        const a=Math.random() * 100;
        
      const newFilm = {
        yonetmen: film.yonetmen,
        link: film.link,
        filmName: film.filmName,
        id:a
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
  deleteUpdate(film){
      for(let i=0;i<this.films.length;i++){
        if(this.films[i]===film){
          film.link=this.films.link
          film.filmName=this.films.filmName
          film.yonetmen=this.films.yonetmen
        }
      }
      this.addFilm(film)

  }
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
