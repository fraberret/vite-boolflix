<script>
import axios from 'axios';
import Flags from './components/Flags.vue';


export default {
    name: 'App',
    components: {
        Flags
    },
    data() {
        return {
            allContents: [],
            contentKey: [],
            searchText: ''
        }
    },
    methods: {
        callApi(url) {
            axios.get(url)
                .then(resp => {

                    this.allContents = this.allContents.concat(resp.data.results)
                })

        },
        searchFilms() {
            this.allContents = []
            console.log(this.searchText);
            this.callApi(`https://api.themoviedb.org/3/search/movie?api_key=b1003d70cc2d6eaae13e67d404d98fdd&query=${this.searchText}`)
        },
        searchTvSeries() {
            this.allContents = []
            console.log(this.searchText);
            this.callApi(`https://api.themoviedb.org/3/search/tv?api_key=b1003d70cc2d6eaae13e67d404d98fdd&language=it_IT&query=${this.searchText}`)
        },
        convertVote(vote) {
            const convertedVote = Math.ceil(vote / 2);
            const stars = Array(5).fill('☆');

            return stars.join('');
        }
    }
}
</script>

<template>
    <div class="search_bar">
        <input type="text" v-model="searchText" @keyup.enter="searchFilms(); searchTvSeries()">
        <button @click="searchFilms(); searchTvSeries()">Search</button>
    </div>

    <div class="results">
        <ul v-for=" content  in  allContents ">


            <!-- Titolo -->
            <li>
                <h3>{{ content.title || content.name }}</h3>
            </li>

            <li>
                <img :src="`https://image.tmdb.org/t/p/w342/${content.poster_path}`" alt="">
            </li>

            <!-- Titolo originale -->
            <li>Titolo Originale: {{ content.original_title || content.original_name }}</li>

            <!-- Lingua -->
            <li>Lingua:
                <Flags :language="content.original_language" />
            </li>

            <!-- Voto -->
            <li>Voto: {{ convertVote(content.vote_average) }}</li>

            <!-- Tipo -->
            <li>Tipo: {{ content.original_name ? 'Serie TV' : 'Film' }}</li>

        </ul>
    </div>


</template>

<style></style>
