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
        <div v-show="store.rispostaApiMovie.length > 0">
            <h2>
                Film
            </h2>
        </div>
        <div class="containerCards">
            <div class="flip-card" v-for="(film, index) in this.store.rispostaApiMovie">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/' + 'w342' + film.poster_path" :alt="film.title">
                    </div>
                    <div class="flip-card-back">
                        <p>Titolo: {{ film.title }}</p>
                        <br>
                        <p>Titolo Originale: {{ film.original_title }}</p>
                        <br>
                        <span>Voto: </span>
                        <span v-for="film in store.votiMovie">
                            <i class="fa-solid fa-star"></i>
                        </span>
                        <span v-for="film in (5 - store.votiMovie)">
                            <i class="fa-regular fa-star"></i>
                        </span>
                        <br>
                        <br>
                        <p v-show="store.votiMovie.length > 0">Trama: {{ film.overview }}</p>
                    </div>
                </div>
            </div>
        </div>

        <div v-show="store.rispostaApiTv.length > 0">
            <h2>
                Serie TV
            </h2>
        </div>
        <div class="containerCards">
            <div class="flip-card" v-for="(tv, index) in store.rispostaApiTv">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/' + 'w342' + tv.poster_path" :alt="tv.name">
                    </div>
                    <div class="flip-card-back">
                        <p>Titolo: {{ tv.name }}</p>
                        <br>
                        <p>Titolo Originale: {{ tv.original_name }}</p>
                        <br>
                        <p>Voto: </p>
                        <span v-for="tv in store.votiTv">
                            <i class="fa-solid fa-star"></i>
                        </span>
                        <span v-for="tv in (5 - store.votiTv)">
                            <i class="fa-regular fa-star"></i>
                        </span>
                        <br>
                        <br>
                        <p v-show="store.votiTv.length > 0">Trama: {{ tv.overview }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped>
.flip-card {
    background-color: black;
    height: 300px;
    width: 200px;
    margin: 10px;
    perspective: 1000px;
    box-shadow: 0px 0px 20px 3px #000000;

}

.flip-card-inner {
    position: relative;
    width: 200px;
    height: 300px;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
    position: absolute;
    width: 200px;
    height: 300px;
    backface-visibility: hidden;
}

.flip-card-front {
    background-image: url(../assets/fallbackImg.gif);
    background-repeat: no-repeat;
    background-size: contain;
    background-position-y: center;
    background-color: white;
}

.flip-card-front img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.flip-card-back {
    background-color: black;
    color: white;
    transform: rotateY(180deg);
    overflow-y: scroll;
    padding: 20px;
}

.fa-solid {
    color: rgb(255, 208, 0);
}

.containerMain {
    overflow-y: hidden;
    background-color: rgb(46, 44, 44);

    h2 {
        padding-left: 10px;
        font-size: 2em;
        margin: 10px 0 10px 0;
        color: #DB202C;
    }
}

.containerCards {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: scroll;
    height: 400px;
    padding-top: 20px;
}
</style>