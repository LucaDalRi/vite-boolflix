<script>
import { store } from '../store';
import "/node_modules/flag-icons/css/flag-icons.min.css";
export default {
    name: 'AppMain',
    data() {
        return {
            store,
        };
    },
    methods: {



    },
}
</script>

<template>

    <div class="containerMain">
        <h2>
            Film
        </h2>
        <div v-for="(film, index) in store.rispostaApiMovie[0]">
            <h4>
                <mark>Titolo</mark>
                {{ store.rispostaApiMovie[0][index].title }}
                <mark>Titolo Originale</mark>
                {{ store.rispostaApiMovie[0][index].original_title }}
                <mark>Lingua</mark>
                <span class="fi" :class="'fi-' + store.rispostaApiMovie[0][index].original_language"></span>
                {{ store.rispostaApiMovie[0][index].original_language }}
                <mark>Voto</mark>
                {{ store.rispostaApiMovie[0][index].vote_average }}
                <!-- devo trovare il modo di dare le stelle in base al voto -->
                {{ store.votiMovie[index] }}
                <div>
                    <img :src="'https://image.tmdb.org/t/p/' + 'w342' + store.rispostaApiMovie[0][index].poster_path"
                        :alt="store.rispostaApiMovie[0][index].title">
                </div>
            </h4>
        </div>
        <div>
            <h2>
                Serie tv
            </h2>
            <div v-for="(film, index) in store.rispostaApiTv[0]">
                <h4>
                    <mark>Titolo</mark>
                    {{ store.rispostaApiTv[0][index].name }}
                    <mark>Titolo Originale</mark>
                    {{ store.rispostaApiTv[0][index].original_name }}
                    <mark>Lingua</mark>
                    <span class="fi" :class="'fi-' + store.rispostaApiTv[0][index].original_language"></span>
                    {{ store.rispostaApiTv[0][index].original_language }}
                    <mark>Voto</mark>
                    {{ store.rispostaApiTv[0][index].vote_average }}
                    <div>
                        <img :src="'https://image.tmdb.org/t/p/' + 'w342' + store.rispostaApiTv[0][index].poster_path"
                            :alt="store.rispostaApiTv[0][index].name">
                    </div>
                </h4>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped>
* {
    border: 1px dashed red;
}

img {
    width: 80px;
    height: 100px;
}
</style>