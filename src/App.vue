<template>
  <div class="container">
    <SearchBar @termChange="onSearchChange"></SearchBar>
    <div class="row">
      <VideoDetails
          v-if="video"
          :video="video"></VideoDetails>
      <VideoList
          @onVideoSelect="onVideoSelect"
          :videos="videos"
      ></VideoList>
    </div>
  </div>

</template>

<script>
import axios from 'axios';
import SearchBar from "@/components/SearchBar";
import VideoList from '@/components/VideoList';
import VideoDetails from "@/components/VideoDetails";

const API_KEY = 'secret:-)';

export default {
  name: 'App',
  data() {
    return {
      videos: [],
      video: null
    }
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetails
  },
  methods: {
    onVideoSelect(video) {
      this.video = video;
    },
    onSearchChange(value) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: value
        }
      }).then(response => {
        this.videos = response.data.items;
      })
    }
  }
}
</script>

<style>
.list-group {
  flex: 1 0 auto;
}
</style>