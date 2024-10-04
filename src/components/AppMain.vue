<script>
import { store } from "../store";
import axios from 'axios';
import AppHeader from './AppHeader.vue';
import MainFilmList from './MainFilmList.vue';
import MainSeriesTvList from './MainSeriesTvList.vue'

export default {
    data() {
        return {
            store,
        }
    },
    components: {
        store,
        AppHeader,
        MainFilmList,
        MainSeriesTvList
    },
    methods: {
        getMovieList(){
            const query = this.store.searchedFilm;

            if (!this.store.searchedFilm) {
                axios.get('https://api.themoviedb.org/3/movie/popular?api_key=aea95f4298835f7d0f3d896a8e981b61')
                .then((response) => {
                    this.store.movieList = response.data.results.slice(0, 20);
                })
                .catch((error) => {
                    console.log(error);
                });

                axios.get('https://api.themoviedb.org/3/tv/popular?api_key=aea95f4298835f7d0f3d896a8e981b61&language=it_IT')
                .then((response) => {
                    this.store.seriesTvList = response.data.results.slice(0, 20);
                })
                .catch((error) => {
                    console.log(error);
                });
            } else {
                axios.get('https://api.themoviedb.org/3/search/movie?api_key=aea95f4298835f7d0f3d896a8e981b61&query=' + query)
                .then((response) => {
                    this.store.movieList = response.data.results;
                })
                .catch((error) => {
                    console.log(error);
                });

                axios.get('https://api.themoviedb.org/3/search/tv?api_key=aea95f4298835f7d0f3d896a8e981b61&language=it_IT&query=' + query)
                .then((response) => {
                    this.store.seriesTvList = response.data.results;
                })
                .catch((error) => {
                    console.log(error);
                });
            }
        },
        searchFilm(){
            this.store.searchedFilm = this.store.searchedFilm.split(' ').join('+')
            console.log(this.store.searchedFilm)
            this.getMovieList()
        }
    },
    created(){
        this.getMovieList()
    }}
</script>

<template>

    <AppHeader @searched="searchFilm"/>
    <MainFilmList/>
    <MainSeriesTvList/>

</template>

<style scoped lang="scss">
@use '../styles/partials/mixin' as *;
@use '../styles/partials/variable' as *;

</style>