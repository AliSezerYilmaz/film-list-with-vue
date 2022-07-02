<template>
  <div class="container" style="margin-top: 20px">
    <div class="card row">
      <div class="card-header">Film Projesi</div>
      <div class="card-body">
        <form @submit.prevent="filmiEkle" id="film-form" name="form">
          <div class="form-row">
            <div class="form-group col-md-6">
              <input
                v-model="film.filmName"
                class="form-control"
                type="text"
                name="title"
                id="title"
                placeholder="Film İsmi"
                autocomplete="off"
                required
              />
            </div>
            <div class="form-group col-md-6">
              <input
                v-model="film.yonetmen"
                class="form-control"
                type="text"
                name="director"
                id="director"
                placeholder="Yönetmen"
                autocomplete="off"
                required
              />
            </div>
            <div class="form-group col-md-6">
              <input
                autocomplete="off"
                v-model="film.link"
                class="form-control"
                type="text"
                name="url"
                id="url"
                placeholder="Film Afiş Linki"
                required
              />
            </div>
          </div>
          <button type="submit" class="btn btn-danger">Film Ekleyin</button>
        </form>
        <hr />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "AddFilm",
  data() {
    return {
      film: {
        filmName: "",
        yonetmen: "",
        link: "",
        id:""
      },
    };
  },
  methods: {
    filmiEkle() {
        this.$emit("add:film",this.film)
    },
  },
};
</script>
<style scoped>
</style>