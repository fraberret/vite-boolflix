<template>
    <img :src="flagUrl" :alt="language" width="15">
</template>

<script>

export default {

    name: 'Flags',
    props: {
        language: String
    },

    computed: {
        flagUrl() {

            const flags = {
                it: `/img/it.svg`,
                en: '/img/gb.svg',
                uk: '/img/ua.svg',
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
                pt: '/img/pt.svg',
                th: '/img/th.svg',
                de: '/img/de.svg'


            };
            return flags[this.language.toLowerCase()];
        }
    }

};
</script>
<style>
img {
    border-radius: 50%;
}
</style>