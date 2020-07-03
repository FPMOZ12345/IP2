<template>
  <div>
       <h2>Potvrđeni nadolazeći anime!</h2><hr>
         <b-row>
        <b-col cols="6">
            <b-button @click="fetchNew">Upcoming</b-button>
        </b-col>
        <b-col cols="6">
          <b-button @click="prikazi_sakriji()">{{ prikazi == true ? 'Sakrij detalje' : 'Prikaži detalje' }}</b-button>
        </b-col>
      </b-row><hr>
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
            <b-card-text v-if="prikazi">{{top.title + ' | datum početka: ' + top.start_date + ' | mjesto: ' + top.rank}}</b-card-text>
          </b-card>
        </b-col>
      </b-row>
  </div>
</template>

<script>
export default {
  name: "Upcoming",

  data: function() {
    return {
      array: [],
      prikazi: true
    };
  },

  methods: {
    fetchNew: function() {
      this.axios
        .get("https://api.jikan.moe/v3/top/anime/1/upcoming").then(response => {
          console.log(response.data.top);

          this.array = response.data.top;
        });
    },

    prikazi_sakriji: function() {
      this.prikazi = !this.prikazi;
    },

    
  }
}
</script>

<style>
</style>