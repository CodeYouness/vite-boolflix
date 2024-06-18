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
        },
        getUnstarMovie(movie) {
            return (5 - Math.ceil(movie.vote_average / 2));
        }
    },
}
</script>

<template>
    <h2>Film List</h2>

    <main class="d-flex justify-content-center align-items-center">
        <div class="overflow-x-auto">
            <ul class="d-flex flex-nowrap">
                <li v-for="(film,index) in store.movieList" :key="index" class="d-flex flex-column">

                    <div>
                        <p>Name: {{ film.title }}</p>
                        <p>Original name: {{ film.original_title }}</p>
                        <p>Language: {{ film.original_language }} <span class='fi' :class="'fi-' + film.original_language"></span></p>
                        <p>
                            Vote:
                            <i class="fa-solid fa-star" v-for="n in getStarMovie(film)"></i>
                            <i class="fa-regular fa-star" v-for="n in getUnstarMovie(film)"></i>
                        </p>
                    </div>

                    <div>
                        <img :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" :alt="film.name">
                    </div>

                </li>
            </ul>
        </div>
    </main>

</template>

<style scoped lang="scss">
@use '../styles/partials/mixin' as *;
@use '../styles/partials/variable' as *;
</style>