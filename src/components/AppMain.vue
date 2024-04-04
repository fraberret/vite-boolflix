<script>

import Card from './Card.vue'
export default {
    name: 'AppMain',
    components: {
        Card,
    },
    props: {
        contents: Array
    }

}
</script>

<template>
    <div class="results">
        <Card v-for="contents in contents" :contents="contents" />
    </div>
</template>

<style lang="scss" scoped></style>