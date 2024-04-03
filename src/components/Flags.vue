<template>
    <img :src="flagUrl" :alt="language" width="15">
</template>

<script>

export default {

    props: {
        language: String
    },

    computed: {
        flagUrl() {

            const flags = {
                it: `/img/it.svg`,
                en: '/img/gb.svg',
                es: '/img/es.svg',
                fr: '/img/fr.svg',
                es: '/img/es.svg',
                cn: '/img/cn.svg',
                zh: '/img/cn.svg',
                sh: '/img/sh.svg',
                ja: '/img/jp.svg',
                sv: '/img/sv.svg',
                ko: '/img/kr.svg',
                ru: '/img/ru.svg',
                ca: '/img/es-ct.svg',


            };
            return flags[this.language.toLowerCase()];
        }
    }

};
</script>