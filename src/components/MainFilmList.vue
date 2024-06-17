<script>
import { store } from "../store";
import "/node_modules/flag-icons/css/flag-icons.min.css";

export default {
    data() {
        return {
            store,
        }
    },
    components: {
        store,
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
                <p>flag: <span class='fi' :class="'fi-' + film.original_language"> </span></p>
            </li>
        </ul>
    </main>

</template>

<style scoped>

</style>