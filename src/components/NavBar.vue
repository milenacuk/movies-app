<template>
    <nav class="navbar navbar-light" style="background-color: #e3f2fd;">      
        <router-link class="navbar-brand" to="/movies">Movies</router-link>
        <!-- <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button> -->
        <form class="form-inline my-2 my-lg-0">
             <movie-search/>
      
    </form>
    </nav>
</template>



<script>
import MovieSearch from './MovieSearch.vue'

export default {
    components: {
        MovieSearch
    }
}
</script>
