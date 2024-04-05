<script>
import axios from 'axios'
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';


export default {
    name: 'App',
    components: {
        AppHeader,
        AppMain
    },
    data() {
        return {
            allContents: [],
            searchText: '',
        }
    },
    methods: {

        /* Funzione che riceve il testo di ricerca e il trigger */
        performSearch(searchText) {

            /* Svuota allContents ad ogni ricerca */
            this.allContents = [],

                /* Passa il testo da ricercare */
                this.searchText = searchText;

            /* Invoca la funziona per cercare i film */
            this.searchFilms();

            /* Invoca la funziona per cercare le Serie Tv */
            this.searchTvSeries();
        },

        /* Funzione per fare le chiamate Ajax */
        callApi(url) {
            axios.get(url)
                .then(resp => {

                    /* Unisce gli array di Film e Serie Tv */
                    this.allContents = this.allContents.concat(resp.data.results)
                })

        },
        /* Funzione per richiamare i film */
        searchFilms() {
            console.log(this.searchText);

            /* Chiamata Ajax per recuperare i film cercati */
            this.callApi(`https://api.themoviedb.org/3/search/movie?api_key=b1003d70cc2d6eaae13e67d404d98fdd&query=${this.searchText}`)

        },

        /* Funzione per richiamare le serie Tv */
        searchTvSeries() {
            console.log(this.searchText);

            /* Chiamata Ajax per recuperare le serie cercate */
            this.callApi(`https://api.themoviedb.org/3/search/tv?api_key=b1003d70cc2d6eaae13e67d404d98fdd&language=it_IT&query=${this.searchText}`)
        },

    },
    mounted() {

        console.log(this.searchText);
        /* Chiamata Ajax per far comparire da subito i film in pagina */
        this.callApi(`https://api.themoviedb.org/3/discover/movie?api_key=b1003d70cc2d6eaae13e67d404d98fdd`)


    }

}
</script>

<template>

    <AppHeader @search="performSearch" />
    <AppMain :contents="allContents" />


</template>

<style></style>
