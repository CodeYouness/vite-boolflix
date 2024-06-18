<script>
import { store } from "../store";
import "/node_modules/flag-icons/css/flag-icons.min.css";
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

export default {
    data() {
        return {
            store,
            FontAwesomeIcon
        }
    },
    components: {
        store,
        FontAwesomeIcon
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
        <h2>Film List</h2>
        <ul>
            <li v-for="(film,index) in store.movieList" :key="index" class="d-flex mb-3">

                <div>
                    <p>name film: {{ film.title }}</p>
                    <p>original name: {{ film.original_title }}</p>
                    <p>language: {{ film.original_language }}</p>
                    <p> average score: {{ film.vote_average }}</p>
                    <p> stars score: <i class="fa-solid fa-star" v-for="n in getStarMovie(film)"></i></p>
                    <p>flag: <span class='fi' :class="'fi-' + film.original_language"></span></p>
                </div>

                <div>
                    <img :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" :alt="film.name">
                </div>

            </li>
        </ul>
    </main>

</template>

<style scoped lang="scss">
@use '../styles/partials/mixin' as *;
@use '../styles/partials/variable' as *;
</style>