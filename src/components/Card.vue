<script>

export default {
    name: 'Card',

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

    <ul>

        <!-- Titolo -->
        <li>
            <h3>{{ contents.title || contents.name }}</h3>
        </li>

        <li>
            <img :src="`https://image.tmdb.org/t/p/w342/${contents.poster_path}`" alt="">
        </li>

        <!-- Titolo originale -->
        <li>Titolo Originale: {{ contents.original_title || contents.original_name }}</li>

        <!-- Lingua -->
        <li>Lingua:
            <Flags :language="contents.original_language" />
        </li>

        <!-- Voto -->
        <li>Voto: {{ convertVote(contents.vote_average) }}</li>

        <!-- Tipo -->
        <li>Tipo: {{ contents.original_name ? 'Serie TV' : 'Film' }}</li>

    </ul>

</template>

<style lang="scss" scoped></style>