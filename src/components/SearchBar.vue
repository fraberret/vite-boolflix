<script>

export default {
    name: 'SearchBar',
    data() {
        return {
            searchText: '',
        }
    },

    methods: {
        search() {

            this.$emit('search', this.searchText);
        }
    }

}
</script>

<template>
    <div class="search_bar">
        <input class="form-control me-2" type="text" v-model="searchText" @keyup.enter="search">
        <button class="btn btn-outline-danger my-2 my-sm-0" @click="search">Search</button>
    </div>
</template>


<style>
.search_bar {
    position: absolute;
    right: 0;
    display: flex;
}
</style>