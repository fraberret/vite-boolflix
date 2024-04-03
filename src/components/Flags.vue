<template>
    <img :src="flagUrl" :alt="language" width="15">
</template>

<script>

export default {
    data() {
        return {
            flagUrl: "",
        }
    },
    props: {
        language: String
    },

    mounted() {
        if (this.language == 'it') {
            this.flagUrl = "img/it.svg"
        }
        else if (this.language == 'en') {
            this.flagUrl = "img/gb.svg"
        }
        else if (this.language == 'fr') {
            this.flagUrl = "img/fr.svg"
        }
        else if (this.language == 'es') {
            this.flagUrl = "img/es.svg"
        }
        else if (this.language == 'en') {
            this.flagUrl = "img/gb.svg"
        }
        else if (this.language == 'en') {
            this.flagUrl = "img/gb.svg"
        }
        else if (this.language == 'en') {
            this.flagUrl = "img/gb.svg"
        }
    }

};
</script>