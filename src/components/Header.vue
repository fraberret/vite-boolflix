<script>
import SearchBar from './SearchBar.vue';
import AppLogo from '../AppLogo.vue';

export default {
    name: 'Header',
    components: {
        SearchBar,
        AppLogo
    }
}
</script>

<template>
    <div class="header">
        <AppLogo />
        <SearchBar />
    </div>
</template>


<style></style>