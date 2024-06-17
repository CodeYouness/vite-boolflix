<script>
import { store } from "../store";
import axios from 'axios';
import AppHeader from './AppHeader.vue';
import MainFilmList from './MainFilmList.vue';

export default {
    data() {
        return {
            store,
        }
    },
    components: {
        store,
        AppHeader,
        MainFilmList
    },
    methods: {
        getMovieList(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=aea95f4298835f7d0f3d896a8e981b61&query=' + this.store.searchedFilm)
            .then((response) => {
                // handle success
                // console.log(response.data.results);
                this.store.movieList = response.data.results
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            axios.get('https://api.themoviedb.org/3/search/tv?api_key=aea95f4298835f7d0f3d896a8e981b61&language=it_IT&query=' + this.store.searchedFilm)
            .then((response) => {
                // handle success
                console.log(response.data.results);
                this.store.seriesTvList = response.data.results
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
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

</template>

<style scoped lang="scss">
@use '../styles/partials/mixin' as *;
@use '../styles/partials/variable' as *;

</style>