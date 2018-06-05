<template>
<ul class="list-group col-md-4">
<VideoListItem 
    v-for="singleVideo in videos"
    :video="singleVideo"
    :key="singleVideo.etag"
    @videoSelect = "onVideoSelect"
>
<!-- onVideoSelect為下面的methods -->
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
    props: ['videos'],
    methods:{
        onVideoSelect(video){
            this.$emit('videoSelect',video);
        }
    }

}
</script>



<style>

</style>

