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
      <tbody v-for="film in films" :key="film.id">
        <tr>
          <td v-if="updateId===film.id">
          <input
              type="text"
              v-model="film.link"
              class="form-control"
              id="link"
            />
            </td>
          <td v-else><img :src="film.link" /></td>
          <td  v-if="updateId===film.id"><input
              type="text"
              v-model="film.filmName"
              class="form-control"
              id="filmName"
            /></td>
          <td v-else scope="col">{{ film.filmName }}</td>
          <td v-if="updateId===film.id">
          <input
              type="text"
              v-model="film.yonetmen"
              class="form-control"
              id="yonetmen"
            />
          </td>
          <td v-else scope="col">{{ film.yonetmen }}</td>
          <td v-if="updateId!==film.id">
            <button class="guncelle btn btn-primary" @click="handleUpdate(film)">
              Güncelle
            </button>
            <button
              @click="deleteFilm(film)"
              id="delete-film"
              class="btn btn-danger"
            >
              Filmi Sil
            </button>
          </td>
          <td v-else>
            <button class="guncelle btn btn-primary" @click="handleSave(film)">
              Kaydet
            </button>
            <button
              @click="updateId=null"
              id="delete-film"
              class="btn btn-danger"
            >
              İptal Et
            </button>
          </td>
          
        </tr>
      </tbody>
    </table>
    <hr />
    <button @click="deleteFilms" class="btn btn-dark">
      Tüm Filmleri Temizleyin
    </button>
  </div>
</template>
<script>
export default {
  name: "film-liste",
  props: {
    films: Array,
  },
  data(){
    return{ updateId:null};
  },
  methods: {
    deleteFilms() {
      this.$emit("deleteAll");
    },
    deleteFilm(film) {
      this.$emit("deleteFilm:film", film);
    },
    handleUpdate(film) {
      this.updateId=film.id
    },
    handleSave(film){
      this.$emit("update:film",film);
      this.updateId=null;
    }
  },
};
</script>
<style scoped>
img {
  background: white;
  max-height: 150px;
}
td {
  font-size: 130%;
}
.guncelle{
  margin-right: 2%;
}
</style>