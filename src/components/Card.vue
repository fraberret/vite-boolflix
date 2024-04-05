<script>
import axios from 'axios';
import Flags from './Flags.vue';

export default {
    props: [
        "contents"
    ],
    name: 'Card',

    data() {
        return {
            Ids: this.contents.id,
            cast: []
        }
    },

    components: {
        Flags,
    },

    methods: {
        convertVote(vote) {
            const convertedVote = Math.ceil(vote / 2);
            const stars = Array(5).fill('☆');
            for (let i = 0; i < convertedVote; i++) {
                stars[i] = '★';
            }
            return stars.join('');

        },

        getCast() {
            axios.get(`http://api.themoviedb.org/3/movie/${this.Ids}/casts?api_key=b1003d70cc2d6eaae13e67d404d98fdd`)
                .then(resp => {
                    this.cast.push(resp.data.cast)
                })
        },


        imageUrl(posterPath) {
            if (posterPath) {
                return `https://image.tmdb.org/t/p/w342/${posterPath}`;
            } else {

                return '/img/immagine-non-disponibile.png';
            }
        }
    },
    computed() {
        this.getCast()
    }



}
</script>

<template>

    <div class="col-4 rounded-4">
        <div class="card rounded-4  h-100">
            <div class="overlay rounded-4 p-3">
                <h3>{{ contents.title || contents.name }}</h3>

                <p>Cast: {{ cast }}</p>
                <!--Titolo originale-->
                <p>Titolo Originale: {{ contents.original_title || contents.original_name }}</p>

                <!-- Lingua -->
                <p>Lingua:
                    <Flags :language="contents.original_language" />
                </p>

                <!-- Voto -->
                <p>Voto: {{ convertVote(contents.vote_average) }}</p>

                <!-- Tipo -->
                <p>Tipo: {{ contents.original_name ? 'Serie TV' : 'Film' }}</p>

                <p>Trama: {{ contents.overview }}</p>
            </div>
            <img class="rounded-4" :src="imageUrl(contents.poster_path)" alt="">

            <div class="hide">
                <!-- Titolo -->

            </div>
        </div>
    </div>








</template>

<style>
.overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgb(0, 0, 0);
    transition: opacity 0.3s ease;
    opacity: 0;

    color: white;

}

.card:hover .overlay {
    opacity: 1;

    /* Opacità al passaggio del mouse */
}
</style>