<template>
  <div>
    <h2>Unesite naziv ili dio naziva animea koji želite pronaći!</h2><hr>
      <b-row>
        <b-col cols="4">
          <b-form-input v-model="animeSearch" @keyup.enter="fetchData" placeholder="Enter an anime name.. *"></b-form-input>
        </b-col>

        <b-col cols="4">
          <b-button @click="fetchData">Pretraži</b-button>
        </b-col>
        <b-col cols="4">
          <b-button @click="prikazi_sakriji()">{{ prikazi == true ? 'Sakrij detalje' : 'Prikaži detalje' }}</b-button>
        </b-col>
      </b-row>

      <br />
      <b-row
        style="height: 400px; overflow: hidden; overflow-y: scroll; text-align: center; border: 2px solid;"
      >
        <b-col cols="3" v-for="results in animeList" v-bind:key="'results_' + results.mal_id">
          <br />
          <b-card
            :img-src="results.image_url"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 20rem;"
            class="mb-2"
          >
            <b-card-text v-if="prikazi">{{ results.title}}</b-card-text>
          </b-card>
        </b-col>
      </b-row>
  </div>
</template>

<script>
export default {
  name: "AnimeSearch",

  data: function() {
    return {
      animeSearch: "",
      animeList: [],
      prikazi: true,
    };
  },

  methods: {
    fetchData: function() {
      this.axios
        .get("https://api.jikan.moe/v3/search/anime?limit=20&q=" + this.animeSearch).then(response => {
          console.log(response.data.results);

          this.animeList = response.data.results;
        });
    },

      prikazi_sakriji: function() {
            this.prikazi = !this.prikazi;
          }

  }
};
</script>

<style>
</style>