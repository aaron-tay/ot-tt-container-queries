<template>
  <draggable
    class="dropzone"
    :list="items"
    group="component"
    fallbackTolerance="50"
    forceFallback="true"
    filter=".no-drag"
    itemKey="id">
    <template #item="{ element }">
      <component v-bind:is="element.name" v-bind="element.props"></component>
    </template>
  </draggable>
</template>

<script>
import draggable from "vuedraggable";
import Navigation from './Navigation.vue';
import ImageGallery from "./ImageGallery.vue";
import Card from "./Card.vue";

export default {
  props: ["items"],
  name: 'ComponentDropzone',
  components: {
    draggable,
    Navigation,
    ImageGallery,
    Card
  }
}
</script>