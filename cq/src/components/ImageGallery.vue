<template>
  <div class="image-gallery-container">
    <div class="image-gallery">
      <template v-for="item in items">
        <Card :item="item"/>
      </template>
    </div>
  </div>
</template>

<script>
import stockImages from "./stockImages.json";
import Card from "./Card.vue";

export default {
  // props: [items],
  components: {
    Card
  },
  data() {
    return {
      items: stockImages.slice(0, 5).map(s => ({
        title: s.author,
        bodyText: "abc",
        imgUrl: s.download_url
      }))
    };
  }
};
</script>

<style scoped>
.image-gallery-container {
  container-type: inline-size;
  container-name: imageGallery;
}

.image-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-gap: 1rem;
}

/* could be grid when wide or list when narrow */
/* @container imageGallery (width < 1000px) {
  .image-gallery {
    display: flex;
    flex-direction: column;
  }
} */

/* @container imageGallery (width >= 1000px) { */
  .image-gallery {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }
/* } */
</style>