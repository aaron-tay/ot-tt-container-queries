<template>
  <KeepAlive>
    <Layout>
      <template v-slot:header>
        <ComponentDropzone :items="header"/>
      </template>
      <template v-slot:mainnav>
        <ComponentDropzone :items="mainnav"/>
      </template>
      <template v-slot:main>
        <ComponentDropzone :items="main"/>
      </template>
      <template v-slot:sidenav>
        <ComponentDropzone :items="sidenav"/>
      </template>
      <template v-slot:footer>
        <ComponentDropzone :items="footer"/>
      </template>
    </Layout>
  </KeepAlive>
</template>

<script>
import Layout from './components/PageLayout.vue'
import ComponentDropzone from "./components/ComponentDropzone.vue";
import ImageGallery from './components/ImageGallery.vue';

export default {
  name: 'App',
  components: {
    Layout,
    ComponentDropzone,
    ImageGallery
  },
  data() {
    return {
      header: [{ name: "Navigation" }],
      mainnav: [],
      main: [{ name: "ImageGallery" }],
      sidenav: [],
      footer: []
    };
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

body {
  height: 100vh;
  margin: 0;
  padding: 0;
}
* {
  box-sizing: border-box;
}

.dropzone {
  height: 100%;
  width: 100%;
}
</style>
