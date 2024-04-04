<script>
import Flags from './Flags.vue';

export default {
    name: 'Card',

    components: {
        Flags
    },

    props: {
        contents: Array
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
    }

}
</script>

<template>

    <div class="col">
        <div class="card">
            <img :src="`https://image.tmdb.org/t/p/w342/${contents.poster_path}`" alt="">

            <!-- Titolo -->
            <h3>{{ contents.title || contents.name }}</h3>

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
        </div>
    </div>









</template>

<style></style>