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


</template>

<style lang="scss" scoped></style>