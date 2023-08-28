<template>
<div class="page-wrap">
  <header class="page-header">
    <slot name="header"></slot>
  </header>
  <nav class="page-nav">
    <slot name="mainnav"></slot>
  </nav>
  <main class="page-main">
    <slot name="main"></slot>
  </main>
  <aside class="page-sidebar">
    <slot name="sidenav"></slot>
  </aside>
  <footer class="page-footer">
    <slot name="footer"></slot>
  </footer>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.page-wrap {
  height: calc(100vh);

  display: grid;
  grid-template-columns: minmax(10px, 1fr) minmax(10px, 3fr);
  grid-template-rows: min-content min-content 1fr min-content;
  gap: 1px;

  @media (max-width: 700px) {
    grid-template-columns: 100%;
    grid-template-rows: auto;
    > * {
      grid-column: 1 / -1 !important;
      grid-row: auto !important;
      padding: initial;
    }
  }
}

.page-header {
  grid-column: 1 / -1;
  background: #ffcdd2;
  min-height: 64px;
  width: 100%;
  z-index: 100;
}

.page-sidebar {
  grid-column: 1 / 2;
  grid-row: 2 / 4;
  background: #e1bee7;
}
.page-nav {
  grid-column: 2 / 3;
  background: #bbdefb;
  min-height: 48px;
  width: 100%;
}
.page-main {
  grid-column: 2 / 3;
  background: #dcedc8;
}
.page-footer {
  grid-column: 1 / -1;
  background: #ffecb3;
  min-height: 160px;
  width: 100%;
}
</style>
