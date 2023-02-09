<script>
import { store } from '../store';
import axios from 'axios';
export default {
  name: 'AppHeader',
  data() {
    return {
      store,
      inputSearch: '',
      apiRequestUserMovie: '',
      apiRequestUserTv: '',
    };
  },
  methods: {
    btnSearch() {
      this.store.rispostaApiMovie = [],
      this.store.rispostaApiTv = [],
        this.apiRequestUserMovie = ('https://api.themoviedb.org/3/search/movie?api_key=24435e5d965dae03c4aaa6c71f82d8ad&query=' + this.inputSearch.toLowerCase().replaceAll(' ', '+'));
      axios
        .get(this.apiRequestUserMovie)
        .then((request) => {

          this.store.rispostaApiMovie = request.data.results 
          console.log(this.store.rispostaApiMovie)

          // conversione voti scala 5 e push in store.js
          for ( let i = 0; i < this.store.rispostaApiMovie.length; i++) {
            let votiFilm = this.store.rispostaApiMovie[i].vote_average
            votiFilm = Math.floor(votiFilm / 2)
            this.store.votiMovie = votiFilm
          }
        });

      this.apiRequestUserTv = ('https://api.themoviedb.org/3/search/tv?api_key=24435e5d965dae03c4aaa6c71f82d8ad&query=' + this.inputSearch.toLowerCase().replaceAll(' ', '+'));
      axios
        .get(this.apiRequestUserTv)
        .then((request) => {

          this.store.rispostaApiTv = request.data.results
          console.log(this.store.rispostaApiTv)

        })
    }
  },
  mounted() {


  },
}
</script>

<template>

  <div class="containerHeader">
    <div>
      <h1>
        BOOLFLIX
      </h1>
    </div>
    <div>
      <input placeholder="Cosa Vuoi Cercare?" type="search" name="TitleSearch" id="TitleSearch" v-model="inputSearch"
        @keyup.enter="btnSearch()">
      <button @click="btnSearch()">Cerca</button>
    </div>
  </div>

</template>

<style lang="scss" scoped>

</style>