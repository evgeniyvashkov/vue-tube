<template>
  <ul class="list-group col-md-4">
    <VideoListItem
        @onVideoSelect="onVideoSelect"
        v-for="video in videos"
        :key="video.etag"
        :video="video"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "@/components/VideoListItem";

export default {
  name: 'VideoList',
  props: ['videos'],
  components: {
    VideoListItem
  },
  methods: {
    onVideoSelect(video) {
      this.$emit('onVideoSelect', video);
    }
  }
}
</script>

<style scoped>

</style>