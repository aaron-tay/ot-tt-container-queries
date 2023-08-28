<template>
  <div class="image-gallery-container">
    <div class="image-gallery">
      <template v-for="item in items" :key="item.imgUrl">
        <Card :item="item"/>
      </template>
    </div>
  </div>
</template>

<script>
import stockImages from "./stockImages.json";
import stockText from "./stockText.json";
import Card from "./Card.vue";

function shuffle(list) {
  return list.map(v => ({ v, r: Math.random() }))
    .sort((a, b) => a.r - b.r)
    .map(({ v }) => v);
}
const shuffledImages = shuffle(stockImages);
const shuffledText = shuffle(stockText);

export default {
  props: ["numItems"],
  components: {
    Card
  },
  data() {
    return {
      items: shuffledImages.slice(0, this.numItems ?? 5).map((s, idx) => ({
        title: s.author,
        bodyText: shuffledText.slice(idx, idx+3).join(" "),
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
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-gap: 1rem;
}

/* could be grid when wide or list when narrow */
@container imageGallery (width <= 600px) {
  .image-gallery {
    grid-template-columns: 1fr;
    grid-gap: 5px;
  }
}
</style>