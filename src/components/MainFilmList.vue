<script>
import { store } from "../store";
import CountryFlag from 'vue-country-flag-next'

export default {
    data() {
        return {
            store
        }
    },
    components: {
        store,
        CountryFlag
    }
}
</script>

<template>

    <main>
        <ul>
            <li v-for="(film,index) in store.movieList" :key="index">
                <p>
                    name film: {{ film.title }}
                </p>
                <p>original name: {{ film.original_title }}</p>
                <p>language: {{ film.original_language }}</p>
                <p> average score: {{ film.vote_average }}</p>
                <p>flag: <country-flag :country='film.original_language' size='small'/></p>
            </li>
        </ul>
    </main>

</template>

<style scoped>

</style>