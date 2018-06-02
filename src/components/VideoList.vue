<template>
<ul class="list-group">
<VideoListItem 
    v-for="singleVideo in videos"
    :video="singleVideo"
    :key="singleVideo.etag"
>

</VideoListItem>
</ul>
    
</template>


<script>
import VideoListItem from './VideoListItem'
export default {
    name:'VideoList',
    components:{
        VideoListItem
    },
    props: ['videos']

}
</script>



<style>

</style>

