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
        <div>
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
                        <p>Titolo Originale: {{ film.original_title }}</p>
                        <span>Voto: </span>
                        <span v-for="i in store.votiMovie">
                            <i class="fa-solid fa-star"></i>
                        </span>
                        <span v-for="i in (5 - store.votiMovie)">
                            <i class="fa-regular fa-star"></i>
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div>
            <h2>
                Serie TV
            </h2>
        </div>
        <div class="containerCards">
            <div class="flip-card" v-for="(tv, index) in this.store.rispostaApiTv">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/' + 'w342' + tv.poster_path" :alt="tv.name">
                    </div>
                    <div class="flip-card-back">
                        <p>Titolo: {{ tv.name }}</p>
                        <p>Titolo Originale: {{ tv.original_name }}</p>
                        <p>Voto: </p>
                        <span v-for="index in store.votiTv">
                            <i class="fa-solid fa-star"></i>
                        </span>
                        <span v-for="index in (5 - store.votiTv)">
                            <i class="fa-regular fa-star"></i>
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped>
.flip-card {
    background-color: transparent;
    height: 300px;
    width: calc(100% / 10);
    margin: 10px;
    perspective: 1000px;

}

.flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
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
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    border: 2px solid black;
}

.flip-card-front{
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
}
.fa-solid {
    color: rgb(255, 208, 0);
}

.containerMain {
    min-height: calc(100vh - 80px);
    width: 100vw;
    overflow-y: scroll;
    background-color: gray;
    h2{
        text-align: center;
        font-size: 2em;
        margin: 10px 0 10px 0;
    }
}

.containerCards {
    height: 100%;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
}
</style>