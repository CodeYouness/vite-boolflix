<script>
import { store } from '../store';

export default {
    data() {
        return {
            store
        }
    },
}
</script>

<template>
    <header>
        <nav class="navbar navbar-expand bg-dark">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">Boolflix</a>
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="#">Home</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">Serie TV</a>
                        </li>
                        <li class="nav-item">
                        <a class="nav-link" href="#">Film</a>
                        </li>
                    </ul>
                    <div class="d-flex">
                        <input class="form-control me-2" placeholder="Search" v-model="store.searchedFilm" @keyup.enter="$emit('searched')">
                        <button class="btn btn-outline-success" @click="$emit('searched')">Search</button>
                    </div>
                
            </div>
        </nav>
    </header>
</template>

<style scoped lang="scss">
@use '../styles/partials/mixin' as *;
@use '../styles/partials/variable' as *;

.navbar-brand {
    color: red;
    text-transform: uppercase;
}

</style>