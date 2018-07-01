<template>
  <div class="container">
    <app-search-bar @searchTermChange='searchTermChanged'></app-search-bar>
    <div class="row">
      <app-video-detail :video="selectedVideo"></app-video-detail>
      <app-video-list :videos='videos' @videoSelect='onVideoSelect'></app-video-list>
    </div>
  </div>
</template>

<script>
import SearchBar from './SearchBar.vue';
import VideoList from './VideoList.vue';
import VideoDetail from './VideoDetail.vue';
import axios from 'axios';


export default {
  name: 'App',
  data(){
   return {
      videos: [],
      selectedVideo: null
   }
  },
  methods: {
    searchTermChanged(searchTerm){
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(res => this.videos = res.data.items)
    },
    onVideoSelect(video){
      return this.selectedVideo = video
    }
  },
  components: {
    appSearchBar: SearchBar,
    appVideoList: VideoList,
    appVideoDetail: VideoDetail
  }
}
</script>
<style scoped>

</style>
