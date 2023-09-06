<template>
  <div class="image-gallery-container">
    <div class="no-drag">
      <button @click.stop.prevent="removeItems">-</button>
      <button @click.stop.prevent="addItems">+</button>
    </div>
    <div class="image-gallery">
      <template v-for="item in visibleItems" :key="item.imgUrl">
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
  props: ["maxItems"],
  components: {
    Card
  },
  data() {
    return {
      items: shuffledImages.slice(0, this.maxItems ?? 5).map((s, idx) => ({
        title: s.author,
        bodyText: shuffledText.slice(idx, idx+3).join(" "),
        imgUrl: s.download_url
      })),
      numItems: 5
    };
  },
  computed: {
    visibleItems() {
      return this.items.slice(0, this.numItems);
    }
  },
  methods: {
    addItems() {
      this.numItems = Math.min(this.numItems + 1, this.maxItems);
    },
    removeItems() {
      this.numItems = Math.max(0, this.numItems - 1);
    }
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