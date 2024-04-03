<script>
import axios from 'axios';

export default {
    name: 'App',
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
                    this.films = resp.data.results
                })




        },
        searchFilms() {
            console.log(this.searchText);
            this.callApi(`https://api.themoviedb.org/3/search/movie?api_key=b1003d70cc2d6eaae13e67d404d98fdd&query=${this.searchText}`)
        }
    }
}
</script>

<template>
    <div class="search_bar">
        <input type="text" v-model="searchText">
        <button @click="searchFilms">Search</button>
    </div>

    <div class="results">
        <ul v-for="film in films">
            <li>
                <h3>{{ film.title }}</h3>
            </li>
            <li>Titolo Originale: {{ film.original_title }}</li>
            <li>Lingua: {{ film.original_language }}</li>
            <li>Voto: {{ film.vote_average }}</li>

        </ul>
    </div>

</template>

<style></style>
