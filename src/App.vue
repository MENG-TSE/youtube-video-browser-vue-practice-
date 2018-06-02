<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList :videos="videos"></VideoList>   
        <!-- 右邊的videos => the name of the property we want to share  in the parent-->
        <!-- 左邊的videos  => the name of the property wa want to have show up inside the child -->
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
const API_KEY ='AIzaSyBjSqpQChtV1o_zU5vKgRPCsXixS1KA1ik' ;
// 'AIzaSyCx95SsPV4GKc25aVF7Ix_aCcgDPGaZQ7M'
export default {
    name: 'App',
    components: {
        SearchBar : SearchBar,
        VideoList
    },
    data (){
        return { videos: [] };
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
            .then(response => {
                this.videos =  response.data.items;
            });
        }
    }
}
</script>


<style>

</style>

