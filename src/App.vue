<template>
  <b-container style="padding: 0px;">
    <div id="app">
      <div class="jumbotron text-center">
        <b-jumbotron
          b-jumbotron
          class="font-weight-bold"
          bg-variant="dark"
          text-variant="white"
          header="Anime tražilica"
          lead="Pronađite anime i likove po njihovom nazivu, ili provjerite trenutan ranking!"
          style="padding:5px;"
        ></b-jumbotron>
      <b-tabs
        content-class="mt-4"
        justified
        active-nav-item-class="font-weight-bold text-uppercase text-danger"
      >
        <b-tab title="Anime Search" active>
          <AnimeSearch />
        </b-tab>
        <b-tab title="Character Search">
          <CharacterSearch />
        </b-tab>
        <b-tab title="Rankings">
          <Rankings />
      </b-tab>
       <b-tab title="Upcoming">
         <Upcoming />
      </b-tab>
      </b-tabs>
    </div>
  </div>
  </b-container>
</template>

<script>
import AnimeSearch from "./components/AnimeSearch";
import CharacterSearch from "./components/CharacterSearch";
import Rankings from "./components/Rankings";
import Upcoming from "./components/Upcoming"
export default {
  name: "App",
  components: {
    AnimeSearch,
    CharacterSearch,
    Rankings,
    Upcoming
  }
};
</script>

