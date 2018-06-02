<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
const API_KEY ='AIzaSyBjSqpQChtV1o_zU5vKgRPCsXixS1KA1ik' ;
// 'AIzaSyCx95SsPV4GKc25aVF7Ix_aCcgDPGaZQ7M'
export default {
    name: 'App',
    components: {
        SearchBar : SearchBar
    },
    methods: {

        onTermChange: function(searchTerm){
            axios.get('https://www.googleapis.com/youtube/v3/search',{
                params:{
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm      ///q = query
                }
            })
            .then(response => console.log(response));
        }
    }
}
</script>


<style>

</style>

