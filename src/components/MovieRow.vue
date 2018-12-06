<template>
    <!-- <table class="table table-striped">
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
            <tbody> -->
                <tr :class="{ 'selectedMovieBackground' : isSelected }">                  
                    <td>{{ movie.title }}</td>
                    <td>{{ movie.director }}</td>                   
                    <td>
                        <img :src="movie.imageUrl" alt="">
                    </td>
                    <td>{{ movie.duration }}</td>
                    <td>{{ movie.relaseData }}</td>
                    <td>{{ movie.genre }}</td>
                    <td><button  class="btn btn-info" @click='selectMovie'>Select</button></td>               
                    
                </tr>
            <!-- </tbody>
        </table> -->
</template>



<script>
export default {
    props:{
        //  ['movie'],
        movie: { 
            type: Object
            }
    },
    data(){
        return{
            isSelected: false,
            
        }
    },
    methods: {
        selectMovie(){
            if(!this.isSelected){
                 this.isSelected = true;
                 this.$emit("selected");
            }
            else{
                this.isSelected = false;
                this.$emit('unselected');
            }
        }
    }
}
</script>

<style scoped>
.selectedMovieBackground {
    background-color:chocolate !important;
}
/* tr {
    border-color:blue;
} */
</style>
