<template>
 <div class="col-md-8">
   <div class="ratio ratio-16x9">
     <iframe :src="videoUrl"/>
   </div>
   <div class="details">
     <h4>{{ video && video.snippet.title }}</h4>
     <p>{{ video && video.snippet.description}}</p>
   </div>
 </div>
</template>

<script>
export default {
  name: 'VideoDetails',
  props: ['video'],
  computed: {
    videoUrl() {
      return `https://www.youtube.com/embed/${this.video?.id.videoId}`
    }
  }
}
</script>

<style scoped>
.details {
  border-radius: 4px;
  border: 1px solid #ddd;
  padding: 10px;
  margin-top: 20px;
}
</style>

