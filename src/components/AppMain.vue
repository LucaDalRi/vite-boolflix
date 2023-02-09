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
        <div v-for="(film, index) in this.store.rispostaApiMovie">
            <h4>
                <mark>Titolo</mark>
                {{ film.title }}
                <mark>Titolo Originale</mark>
                {{ film.original_title }}
                <mark>Lingua</mark>
                <span class="fi" :class="'fi-' + film.original_language"></span>
                {{ film.original_language }}
                <mark>Voto</mark>
                <span v-for="i in store.votiMovie">
                    ★
                </span>
                <span v-for="i in (5 - store.votiMovie)">
                    ☆
                </span>
                <div>
                    <img :src="'https://image.tmdb.org/t/p/' + 'w342' + film.poster_path" :alt="film.title">
                </div>
            </h4>
        </div>
        <h2>
            Serie tv
        </h2>
        <div>
            <div v-for="(tv, index) in this.store.rispostaApiTv">
                <h4>
                    <mark>Titolo</mark>
                    {{ tv.name }}
                    <mark>Titolo Originale</mark>
                    {{ tv.original_name }}
                    <mark>Lingua</mark>
                    <span class="fi" :class="'fi-' + tv.original_language"></span>
                    {{ tv.original_language }}
                    <mark>Voto</mark>
                    <span v-for="i in store.votiTv">
                        ★
                    </span>
                    <span v-for="i in (5 - store.votiTv)">
                        ☆
                    </span>
                    <div>
                        <img :src="'https://image.tmdb.org/t/p/' + 'w342' + tv.poster_path" :alt="tv.name">
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