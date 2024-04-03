<script>
import { state } from './state'

export default {
    name: 'App',
    data() {
        return {
            state
        }
    }
}
</script>

<template>
    <h1>{{ state.message }}</h1>
</template>

<style></style>
