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
                <tr>
                    <td>{{ movie.title }}</td>
                    <td>{{ movie.director }}</td>                   
                    <td>
                        <img :src="movie.imageUrl" alt="">
                    </td>
                    <td>{{ movie.duration }}</td>
                    <td>{{ movie.relaseData }}</td>
                    <td>{{ movie.genre }}</td>
                    
                </tr>
            <!-- </tbody>
        </table> -->
</template>



<script>
export default {
    props: ['movie']
}
</script>
