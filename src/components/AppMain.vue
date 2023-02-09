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
    <!-- <div class="containerMn"> -->
    <!-- <div v-for="(film, index) in this.store.rispostaApiMovie" class="card">
            <h4>
                <mark>Titolo</mark>
                {{ film.title }}
                <mark>Titolo Originale</mark>
                {{ film.original_title }}
                <mark>Lingua</mark>
                <span class="fi" :class="'fi-' + film.original_language"></span>
                <mark>Voto</mark>
                <span v-for="i in store.votiMovie">
                    <i class="fa-solid fa-star"></i>
                </span>
                <span v-for="i in (5 - store.votiMovie)">
                    <i class="fa-regular fa-star"></i>
                </span>
                <div>
                    <img :src="'https://image.tmdb.org/t/p/' + 'w342' + film.poster_path" :alt="film.title">
                </div>
            </h4>
        </div> -->
    <!-- <h2>
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
                        <i class="fa-solid fa-star"></i>
                    </span>
                    <span v-for="i in (5 - store.votiTv)">
                        <i class="fa-regular fa-star"></i>
                    </span>
                    <div>
                        <img :src="'https://image.tmdb.org/t/p/' + 'w342' + tv.poster_path" :alt="tv.name">
                    </div>
                </h4>
            </div>
        </div> -->
    <div class="containerMain">
        <div>
            <h2>
                Film
            </h2>
        </div>
        <div class="containerCards">
            <div class="card" v-for="(film, index) in this.store.rispostaApiMovie">
                <img :src="'https://image.tmdb.org/t/p/' + 'w342' + film.poster_path" :alt="film.title">
            </div>
        </div>

        <div>
            <h2>
                Serie TV
            </h2>
        </div>
        <div class="containerCards">
            <div class="card" v-for="(tv, index) in this.store.rispostaApiTv">
                <img :src="'https://image.tmdb.org/t/p/' + 'w342' + tv.poster_path" :alt="tv.name">
            </div>
        </div>
    </div>
    <!-- </div> -->

</template>

<style lang="scss" scoped>
* {
    border: 1px dashed red;
}

img {
    width: 80px;
    height: 100px;
}

.fa-solid {
    color: rgb(255, 208, 0);
}

.containerMain {
    min-height: calc(100vh - 80px);
    width: 100vw;
    overflow-y: scroll;
}

.containerCards {
    height: 100%;
    width: 100%;
    display: flex;
    flex-wrap: wrap;

    .card {
        height: 300px;
        width: calc(100% / 10);
        margin: 10px;
        & :hover{
            filter: brightness(0.3);
            
        }

        img {
            height: 100%;
            width: 100%;
            object-fit: cover;
        }
    }
}
</style>