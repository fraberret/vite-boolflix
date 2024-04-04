<script>
import axios from 'axios'
import Card from './Card.vue'
export default {
    name: 'AppMain',
    components: {
        Card
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
    }
}
</script>

<template>
    <div class="results">

    </div>
</template>

<style lang="scss" scoped></style>