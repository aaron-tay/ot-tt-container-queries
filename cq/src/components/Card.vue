<template>
  <div class="card-container">
    <div class="card">
      <div class="card__cover">
        <img class="card__image" :src="item.imgUrl">
      </div>
      <div class="card__content">
        <div class="title">
          {{item.title}}
        </div>
        <div class="body">
          {{item.bodyText}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    item: Object,
  },
};
</script>

<style scoped>
.card {
  border: 1px solid #ccc;
  border-radius: 3px;
  background: white;
  overflow: hidden;
}
.card__cover {
  display: block;
}

.card__image {
  aspect-ratio: 1 / 1;
  width: 100%;
  object-fit: cover;
}
.title {
  font-weight: bold;
}

.card-container {
  container-type: inline-size;
  container-name: card;
  width: 100%;
  height: 100%;
  /* max-width: 500px; */
}

@container card (width < 250px) {
  .card {
    display: flex;
    flex-direction: row;
    gap: 5px;
  }
  .card__cover {
    max-width: 200px;
  }
  .title {
    font-size: 2rem;
  }
}

@container card (width >= 250px) {
  .card {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    gap: 10px;
  }
  .card__cover {
    max-width: 200px;
  }
  .card__content {
  }
}
</style>