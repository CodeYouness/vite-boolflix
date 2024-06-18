<script>
import { store } from "../store";
import "/node_modules/flag-icons/css/flag-icons.min.css";

export default {
    data() {
        return {
            store
        }
    },
    components: {
        store
    },
    methods: {
        getStarMovie(movie) {
            return Math.ceil(movie.vote_average / 2);
        }
    },
}
</script>

<template>

    <main>
        <h2>Series TV List</h2>
        <ul>
            <li v-for="(series,index) in store.seriesTvList" :key="index" class="d-flex">
                <div>
                    <p>name film: {{ series.name }}</p>
                    <p>original name: {{ series.original_name }}</p>
                    <p>language: {{ series.original_language }}</p>
                    <p> average score: {{ series.vote_average }}</p>
                    <p> stars score: <i class="fa-solid fa-star" v-for="n in getStarMovie(film)"></i></p>
                    <p>flag: <span class='fi' :class="'fi-' + series.original_language"> </span></p>
                </div>
                <div>
                    <img :src="'https://image.tmdb.org/t/p/w342' + series.poster_path" :alt="series.name">
                </div>
            </li>
        </ul>
    </main>

</template>

<style scoped lang="scss">
@use '../styles/partials/mixin' as *;
@use '../styles/partials/variable' as *;
</style>