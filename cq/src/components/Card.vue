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
  name: "UiCard",
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
}

@container card (max-width: 300px) {
  .card {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
  }
  .card__content {
    padding: 5px 5px;
    .body {
      display: -webkit-box;
      -webkit-line-clamp: 3;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }
  }
}

@container card (min-width: 301px) and (max-width: 600px) {
  .card {
    display: flex;
    flex-wrap: nowrap;
  }
  .card__cover {
    max-width: 20cqw;
  }
  .card__content {
    padding: 5px 5px;
    .body {
      display: -webkit-box;
      -webkit-line-clamp: 3;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }
  }
}

@container card (min-width: 601px) {
  .card {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
  }
  .card__cover {
    max-width: 40cqw;
  }
  .card__content {
    padding: 5px 5px;
    .title {
      font-size: 3em;
    }
    .body {
      font-size: max(1.5rem, 1.5rem + 1cqw);
    }
  }
}
</style>