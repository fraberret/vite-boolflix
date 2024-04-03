<script>


export default {
    name: 'App',
    data() {
        return {
            searchText: ''
        }
    },
    methods: {
        searchFilms() {
            console.log(this.searchText);
        }
    }
}
</script>

<template>
    <div class="search_bar">
        <input type="text" v-model="searchText">
        <button @click="searchFilms">Search</button>
    </div>

</template>

<style></style>
