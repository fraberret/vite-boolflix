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
            Ids: []
        }
    },
    methods: {



        performSearch(searchText) {

            this.allContents = [],
                this.searchText = searchText;
            this.searchFilms();
            this.searchTvSeries();

        },

        callApi(url) {
            axios.get(url)
                .then(resp => {

                    this.allContents = this.allContents.concat(resp.data.results)
                    console.log(this.allContents);

                    this.Ids = [];

                    this.allContents.forEach(content => {
                        this.Ids.push(content.id);
                    })
                    console.log(this.Ids);
                })

        },

        searchFilms() {
            console.log(this.searchText);
            this.callApi(`https://api.themoviedb.org/3/search/movie?api_key=b1003d70cc2d6eaae13e67d404d98fdd&query=${this.searchText}`)

        },
        searchTvSeries() {
            console.log(this.searchText);
            this.callApi(`https://api.themoviedb.org/3/search/tv?api_key=b1003d70cc2d6eaae13e67d404d98fdd&language=it_IT&query=${this.searchText}`)
        },

        cast() {
            this.Ids.forEach(id => {

            })
        }


    },
    mounted() {

        console.log(this.searchText);
        this.callApi(`https://api.themoviedb.org/3/discover/movie?api_key=b1003d70cc2d6eaae13e67d404d98fdd`)


    }

}
</script>

<template>

    <AppHeader @search="performSearch" />
    <AppMain :contents="allContents" />


</template>

<style></style>
