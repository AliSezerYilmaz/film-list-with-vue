<template>
     <div class="card-body">
        <hr />
        <h5 class="card-title" id="films-title">Filmler</h5>

        <hr />
        <table class="table table-dark">
          <thead>
            <tr>
              <th scope="col">Film Afişi</th>
              <th scope="col">Film İsmi</th>
              <th scope="col">Yönetmen</th>
            </tr>
          </thead>
          <tbody v-for="film in films" :key="film.filmName">
            <tr>
              <img :src="film.link">
              <td scope="col">{{film.filmName}}</td>
              <td scope="col">{{film.yonetmen}}</td>
              <td><button @click="deleteFilm(film)"  id="delete-film" class="btn btn-danger">Filmi Sil</button></td>
            </tr>
          </tbody>
        </table>
        <hr />
        <button @click="deleteFilms" class="btn btn-dark"
          >Tüm Filmleri Temizleyin</button
        >
      </div>
</template>
<script>
export default {
    name: "film-liste",
  props:{
    films: Array
  },
  methods:{
    deleteFilms(){
      this.$emit("deleteAll")
    },
    deleteFilm(film){
      this.$emit("deleteFilm:film",film)

    }
  }
}
</script>
<style scoped>
img{
  background: white;
  max-height: 150px;
}
td{
  font-size: 130%;
}

</style>