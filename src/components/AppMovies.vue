<template>
    <div>
        <br>        
         <table class="table table-striped">
            <thead>
                <tr>
                    <th scope="col">Title</th>
                    <th scope="col">Director</th>
                    <th scope="col">ImageUrl</th>
                    <th scope="col">Duration</th>
                    <th scope="col">Relase Data</th>
                    <th scope="col">Genre</th>
                </tr>
            </thead>
            <tbody>
                                    
                    <MovieRow v-for='movie in filteredMovies' :key='movie.id' :movie="movie"/>
                
                </tbody>
        </table>
            
    </div>
</template>

<script>
import { movies } from '../services/Movies.js'
import MovieRow from './MovieRow.vue'

export default {
    data(){
        return{
            movies:[],
            term: ''
        }
    },
    beforeRouteEnter(to,from,next){
        movies.getAll().then(response => {
            next(vm => {
                vm.movies = response.data;
            })         
        })
        
    },
    components: {
        MovieRow
    },
    computed: {
        filteredMovies(){           
            return this.movies.filter(movie => {
                return movie.title.toLowerCase().includes(this.term.toLowerCase())});
        }
    },
    created (){
        window.EventHub.$on('search', (term)=> {
            this.term = term;
        })
    }
}
</script>
