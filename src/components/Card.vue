<script>
export default {
    name: 'Card',
}
</script>

<template>

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
</template>

<style lang="scss" scoped></style>