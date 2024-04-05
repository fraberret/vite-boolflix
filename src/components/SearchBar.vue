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
            if (this.searchText != '') {
                this.$emit('search', this.searchText);
            }

        }
    }

}
</script>

<template>
    <div class="search_bar">
        <input class="form-control me-2 bg-black rounded-0 text-white" type="text" v-model="searchText"
            @keyup.enter="search" placeholder="Cerca">
        <button class="btn btn-outline-danger my-2 my-sm-0 rounded-0" @click="search">Cerca</button>
    </div>
</template>


<style>
.search_bar {
    position: absolute;
    right: 0;
    display: flex;

}

input::-webkit-input-placeholder {
    color: rgba(255, 254, 254, 0.584) !important;
}
</style>