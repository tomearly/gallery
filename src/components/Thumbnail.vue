<template>
  <div class="thumbnail">
    <a :href="thumbLinkUrl"><img :alt="altDescription" :src="thumbUrl" /></a>
    <ThumbnailOverlay
      class="thumbnail-overlay"
      :first-name="firstName"
      :profile-url="profileUrl"
      :thumb-link-url="thumbLinkUrl">
    </ThumbnailOverlay>
  </div>
</template>

<script>
import ThumbnailOverlay from "@/components/ThumbnailOverlay";
export default {
  components: {
    ThumbnailOverlay
  },
  props: {
    altDescription: {
      type: String
    },
    profileUrl: {
      type: String
    },
    thumbUrl: {
      type: String
    },
    thumbLinkUrl: {
      type: String
    },
    firstName: {
      type: String
    }
  }
};
</script>

<style lang="scss">
  .thumbnail-overlay {
    position: relative;
    top: -30px;
    background-color: rgba(255, 255, 255, 0.75);
    padding: 8px;
  }

  .thumbnail-overlay:hover {
    background-color: rgba(255, 255, 255, 1);
  }
  
</style>