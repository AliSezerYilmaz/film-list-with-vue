<template>
  <div class="container" style="margin-top: 20px">
    <div class="card row">
      <div class="card-header">Film Projesi</div>
      <div class="card-body">
        <form @submit.prevent="filmiEkle" id="film-form" name="form">
          <div class="form-row">
            <div class="form-group col-md-6">
              <input
              v-model="filmİsmi"
                class="form-control"
                type="text"
                name="title"
                id="title"
                placeholder="Film İsmi"
              />
            </div>
            <div class="form-group col-md-6">
              <input
              v-model="yonetmen"
                class="form-control"
                type="text"
                name="director"
                id="director"
                placeholder="Yönetmen"
              />
            </div>
            <div class="form-group col-md-6">
              <input
              v-model="link"
                class="form-control"
                type="text"
                name="url"
                id="url"
                placeholder="Film Afiş Linki"
              />
            </div>
          </div>
          <button type="submit" class="btn btn-danger">Film Ekleyin</button>
        </form>
        <hr />
      </div>

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
          <tbody v-for="film in filmList" :key="film.filmİsmi" id="films">
            <tr>
              <img :src="link">
              <td scope="col">{{filmİsmi}}</td>
              <td scope="col">{{yonetmen}}</td>
            </tr>
          </tbody>
        </table>
        <hr />
        <a id="clear-films" class="btn btn-dark" href="#"
          >Tüm Filmleri Temizleyin</a
        >
      </div>
    </div>
  </div>
</template>
<script>
export default {
    name: 'FilmList',
    data(){
        return{
            filmİsmi:"",
            yonetmen:"",
            link:"",
            filmList:[]
        }
    },
    methods:{
        filmiEkle(){
      const film = { filmİsmi: this.filmİsmi, yonetmen: this.yonetmen, link: this.link };
      this.filmList.push(film)
        }
    }
};
</script>
<style scoped>
</style>