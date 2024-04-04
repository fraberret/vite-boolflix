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
            films: [],
            searchText: ''
        }
    },
    methods: {
        callApi(url) {
            axios.get(url)
                .then(resp => {

                    this.films = this.films.concat(resp.data.results)
                })

        },
        searchFilms() {
            this.films = []
            console.log(this.searchText);
            this.callApi(`https://api.themoviedb.org/3/search/movie?api_key=b1003d70cc2d6eaae13e67d404d98fdd&query=${this.searchText}`)
        },
        searchTvSeries() {
            this.films = []
            console.log(this.searchText);
            this.callApi(`https://api.themoviedb.org/3/search/tv?api_key=b1003d70cc2d6eaae13e67d404d98fdd&language=it_IT&query=${this.searchText}`)
        }
    }
}
</script>

<template>
    <div class="search_bar">
        <input type="text" v-model="searchText" @keyup.enter="searchFilms">
        <button @click="searchFilms(); searchTvSeries()">Search</button>
    </div>

    <div class="results">
        <ul v-for=" film  in  films ">
            <li>
                <h3>{{ film.title }}</h3>
                <h3>{{ film.name }}</h3>

            </li>
            <li>Titolo Originale: {{ film.original_title }}</li>
            <li>Lingua:
                <Flags :language="film.original_language" />
            </li>
            <li>Voto: {{ film.vote_average }}</li>

        </ul>
    </div>


</template>

<style></style>
