<script>
import { store } from "../store";

export default {
    data() {
        return {
            store
        }
    },
    components: {
        store
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
                <p> original name: {{ film.vote_average }}</p>
            </li>
        </ul>
    </main>

</template>

<style scoped>

</style>