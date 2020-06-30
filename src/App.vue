<template>
  <div 
    id="app"
    v-if="photos.results"
    class="gallery">
    <thumbnail
      v-for="photo of photos.results"
      :key="photo.id"
      :alt-description="photo.alt_description"
      :profile-url="photo.user.links.html"
      :thumb-url="photo.urls.thumb"
      :thumb-link-url="photo.links.html"
      :first-name="photo.user.first_name">
    </thumbnail>
  </div>
</template>

<script>
import dataService from "@/api/dataService";
import Thumbnail from "@/components/Thumbnail";

export default {
  name: "App",
  components: {
    Thumbnail
  },
  mounted() {
    this.loadPhotos();
  },
  methods: {
    async loadPhotos() {
      this.photos = await dataService.getPhotos(
        "query=paris&color=black_and_white&orientation=landscape"
      );
    }
  },
  data() {
    return {
      photos: {}
    };
  }
};
</script>

<style lang="scss">
.gallery {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-gap: 24px;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
</style>
