<script>
import Flags from './components/Flags.vue';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';


export default {
    name: 'App',
    components: {
        Flags,
        AppHeader,
        AppMain
    },
    data() {
        return {
            allContents: [],

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

    <AppHeader />
    <AppMain />


</template>

<style></style>
