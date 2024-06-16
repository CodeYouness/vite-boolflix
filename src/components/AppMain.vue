<script>
import { store } from "../store";
import axios from 'axios';
import AppHeader from './AppHeader.vue';

export default {
    data() {
        return {
            store,
        }
    },
    components: {
        store,
        AppHeader
    },
    methods: {
        getMovieList(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=aea95f4298835f7d0f3d896a8e981b61&query=ritorno+al+futuro')
            .then((response) => {
                // handle success
                console.log(response.data.results);
                this.store.cardList = response.data.results
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
        },
        searchFilm(){
            console.log(this.store.searchedFilm)
            console.log('daje')
        }
    },
    created(){
        this.getMovieList()
    }}
</script>

<template>

    <AppHeader @searched="searchFilm"/>
    <main>

    </main>
</template>

<style scoped lang="scss">
@use '../styles/partials/mixin' as *;
@use '../styles/partials/variable' as *;

</style>