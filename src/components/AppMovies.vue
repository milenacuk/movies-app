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
                    <th scope="col"></th>                  
                </tr>
            </thead>
            <tbody>                                 
                <!-- <template v-if="filteredMovies.length"> -->
                    <p v-if="numberSelectedMovies"> Selected Movies: {{numberSelectedMovies}}</p>
                    <!-- <button class="btn btn-info" @click="selectAll">Select all movies</button>
                    <button class="btn btn-dark" @click="deselectAll">Deselect movies</button> -->

                        <!-- <p class="num-of-selected-movies">Selected Movies: {{numberSelectedMovies}}</p> -->
                    <!-- </template> -->
                <MovieRow v-for='movie in filteredMovies' :key='movie.id' 
                        :movie="movie" @selected="movieSelected" @unselected="movieUnselected"/>
                <!-- </template> -->
                <template v-if="!filteredMovies.length">
                     <center> <h3>Movie is not in base!</h3></center>
                </template>

                    
                
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
            term: '',
            numberSelectedMovies: 0,
            // selected: false
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
    },
    methods: {
        movieSelected(){
            this.numberSelectedMovies++;
        },
        movieUnselected(){
            this.numberSelectedMovies--;
        
        // },
        // selectAll(){
            
        // },
        // deselectAll(){
        //     this.numberSelectedMovies;
            
        }

    }
}
</script>
