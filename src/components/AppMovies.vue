<template>
    <div>
        <table border='1'>
            <thead>
                <tr>
                    <th>Title</th>
                    <th>Director</th>
                    <th>ImageUrl</th>
                    <th>Duration</th>
                    <th>Relase Data</th>
                    <th>Genre</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for='movie in movies' :key='movie.id'>
                    <td>{{ movie.title }}</td>
                    <td>{{ movie.director }}</td>
                    <td>{{ movie.imageUrl }}</td>
                    <td>{{ movie.duration }}</td>
                    <td>{{ movie.relaseData }}</td>
                    <td>{{movie.genre }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import { movies } from '../services/Movies.js'

export default {
    data(){
        return{
            movies:[]
        }
    },
    created(){
        movies.get().then(response => {
            this.movies = response.data;
        }).catch(error => {
            console.log(error.response);
        })
    }
}
</script>
