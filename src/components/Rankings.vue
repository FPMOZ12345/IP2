<template>
  <div>
      <h2>Ovdje možete učitate ljestvice vezane za popularnost animea, likova i sl. ! </h2><hr>
      <b-row>
        <b-col cols="3">
            <b-button @click="fetchAnime">Anime</b-button>
        </b-col>

        <b-col cols="3">
          <b-button @click="fetchCharacter">Likovi</b-button>
        </b-col>

        <b-col cols="3">
          <b-button @click="fetchMovie">Filmovi</b-button>
        </b-col>

        <b-col cols="3">
          <b-button @click="fetchManga">Manga</b-button>
        </b-col>
      </b-row><hr>
      <b-button @click="prikazi_sakriji()">{{ prikazi == true ? 'Sakrij detalje' : 'Prikaži detalje' }}</b-button><hr>
       <b-row
        style="height: 400px; overflow: hidden; overflow-y: scroll; text-align: center; border: 2px solid;"
      >
        <b-col cols="3" v-for="top in array"  v-bind:key="'top_' + top.mal_id">
          <br />
          <b-card
            :img-src="top.image_url"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 20rem;"
            class="mb-2"
          >
             <b-card-text v-if="prikazi"> {{top.title + ' | mjesto:' + top.rank}}
            </b-card-text>
            
          </b-card>
        </b-col>
      </b-row>


  </div>
</template>

<script>
export default {
    name: "Rankings",

     data: function() {
    return {
      array: [],
      prikazi:true
    };
  },

  methods: {
    fetchCharacter: function() {
      this.axios
        .get("https://api.jikan.moe/v3/top/characters").then(response => {
          console.log(response.data.top);

          this.array = response.data.top;
        });
    },

    fetchAnime: function(){
        this.axios
        .get("https://api.jikan.moe/v3/top/anime").then(response => {
          console.log(response.data.top);

          this.array = response.data.top;
        });

    },

    fetchMovie: function(){
        this.axios
        .get("https://api.jikan.moe/v3/top/anime/1/movie").then(response => {
          console.log(response.data.top);

          this.array = response.data.top;
        });
    },

     fetchManga: function(){
        this.axios
        .get("https://api.jikan.moe/v3/top/manga").then(response => {
          console.log(response.data.top);

          this.array = response.data.top;
        });
    },

     prikazi_sakriji: function() {
      this.prikazi = !this.prikazi;
    }

  }
}
</script>

<style>

</style>