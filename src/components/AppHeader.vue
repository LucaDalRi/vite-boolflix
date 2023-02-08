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
      store.rispostaApiMovie = [],
        store.rispostaApiTv = [],
        this.apiRequestUserMovie = ('https://api.themoviedb.org/3/search/movie?api_key=24435e5d965dae03c4aaa6c71f82d8ad&query=' + this.inputSearch.toLowerCase().replaceAll(' ', '+'));
      axios
        .get(this.apiRequestUserMovie)
        .then((request) => {

          const rispostaApi = request.data.results;
          store.rispostaApiMovie.push(rispostaApi)
          console.log(store.rispostaApiMovie[0])

          // conversione voti scala 5 e push in store.js
          for ( let i = 0; i < store.rispostaApiMovie[0].length; i++) {
            let votiFilm = store.rispostaApiMovie[0][i].vote_average
            votiFilm = Math.floor(votiFilm / 2)
            
            store.votiMovie.push(votiFilm)
          }
        });

      this.apiRequestUserTv = ('https://api.themoviedb.org/3/search/tv?api_key=24435e5d965dae03c4aaa6c71f82d8ad&query=' + this.inputSearch.toLowerCase().replaceAll(' ', '+'));
      axios
        .get(this.apiRequestUserTv)
        .then((request) => {

          const rispostaApi = request.data.results;
          store.rispostaApiTv.push(rispostaApi)
          console.log(store.rispostaApiTv[0])

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