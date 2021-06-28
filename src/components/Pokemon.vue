<template>
  <div class="container">
    <h1>pokemon</h1>
    <pokemon-search @setPokemonUrl="setPokemonUrl" :apiUrl="apiUrl"></pokemon-search>
    <pokemon-list :imageUrl="imageUrl" :apiUrl="apiUrl" @setPokemonUrl="setPokemonUrl"></pokemon-list>
    <pokemon-detail v-if="showDetail" :pokemonUrl="pokemonUrl" :imageUrl="imageUrl" @closeDetail="closeDetail"></pokemon-detail>
  </div>
</template>

<script>
import PokemonSearch from "@/components/PokemonSearch.vue";
import PokemonList from "@/components/PokemonList.vue";
import PokemonDetail from "@/components/PokemonDetail.vue";
export default {
  components: {
    PokemonSearch,
    PokemonList,
    PokemonDetail,
  },
  data() {
    return {
      imageUrl: "https://pokeres.bastionbot.org/images/pokemon/",
      apiUrl: "https://pokeapi.co/api/v2/pokemon/",
      poekmonUrl: "",
      showDetail: false,
    };
  },
  methods: {
    setPokemonUrl(url) {
      this.pokemonUrl = url;
      this.showDetail = true;
    },
    closeDetail() {
      this.pokemonUrl = "";
      this.showDetail = false;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Acme");
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 10px;
  width: calc(100% - 20px);
  min-height: calc(100vh - 20px);
  background: radial-gradient(#156f99, #0a2e50);
  font-family: "Acme", arial;
  font-size: 1rem;
  font-weight: normal;
}
h1 {
  color: #efefef;
}
</style>
