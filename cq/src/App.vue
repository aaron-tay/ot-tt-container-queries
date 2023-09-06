<template>
  <KeepAlive max="10">
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

export default {
  name: 'App',
  components: {
    Layout,
    ComponentDropzone,
  },
  data() {
    return {
      header: [{ name: "Navigation", id: "N1" }],
      mainnav: [],
      main: [{ name: "ImageGallery", props: { maxItems: 10 }, id: "IG5" }],
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

.sortable-chosen {
  outline: 2px dashed blue;
  opacity: 0.25;
  cursor: pointer;
}
</style>
