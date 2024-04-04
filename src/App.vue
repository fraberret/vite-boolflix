<script>
import axios from 'axios';
import Flags from './components/Flags.vue';
import Header from './components/Header.vue';


export default {
    name: 'App',
    components: {
        Flags,
        Header
    },
    data() {
        return {
            allContents: [],
            contentKey: [],
            searchText: ''
        }
    },
    methods: {

        convertVote(vote) {
            const convertedVote = Math.ceil(vote / 2);
            const stars = Array(5).fill('☆');
            for (let i = 0; i < convertedVote; i++) {
                stars[i] = '★';
            }
            return stars.join('');
        }
    }
}
</script>

<template>

    <Header />

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
