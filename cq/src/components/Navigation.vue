<template>
  <div class="navigation-container">
    <nav class="navigation">
      <ul class="top-level">
        <li>Home</li>
        <li>
          Features
          <ul class="nested-level">
            <li>Spaceships</li>
            <li>Rockets</li>
            <li>Satellites</li>
          </ul>
        </li>
        <li>
          About
          <ul class="nested-level">
            <li>Privacy Policy</li>
            <li>T&C</li>
            <li>Legal</li>
          </ul>
        </li>
        <li>
          <input type="search" placeholder="Search"/>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'UiNavigation',
  props: {}
}
</script>

<style scoped>
ul {
  display: flex;
  gap: 10px;
  list-style-type: none;
  padding: 0;
}

li {
  min-width: 80px;
  &:hover {
    font-weight: bold;
    cursor: pointer;
  }
}

.nested-level {
  font-weight: normal;
  flex-direction: column;
  gap: 0;
  min-width: max-content;
}

.navigation-container {
  container-type: size;
  container-name: navigation;
  width: 100%;
  height: 100%;
}

@media (max-width: 700px) {
  .navigation-container {
    container-type: inline-size;
  }
}

/* sidebar or collapsed mode */
@container navigation (max-width: 700px) {
  *:hover { outline: 5px solid #blue; }
  ul {
    flex-direction: column;
    text-align: left;
  }
  .nested-level {
    margin-left: 10px;
    display: flex;
    position: relative;
    top: initial;
    left: initial;
    gap: 10px;
  }
}

@media (min-width: 701px) {
  @container navigation (width < 80vw) and (height < 100px) {
    .nested-level {
      display: none;
    }
  }
  
  /* 'header' mode' */
  @container navigation (height < 100px) {
    .navigation {
      display: flex;
      height: 100%;
      align-content: center;
      flex-wrap: wrap;
    }
    .top-level > li:hover {
      position: relative;
    }
  
    .nested-level {
      display: none;
      position: absolute;
      left: 0;
      top: 100%;
      background: white;
      outline: 1px solid #ccc;
    }
  
    .top-level > li:hover .nested-level {
      display: flex;
    }
  }
  
  /* when in 'footer' mode */
  @container navigation (width > 80vw) and (height > 100px) {
    ul {
      text-align: left;
      gap: 20px;
    }
    ul > li {
      min-width: 80px;
    }
    .nested-level {
      margin-top: 10px;
      display: flex;
      position: relative;
      top: initial;
      left: initial;
      gap: 10px;
    }
  }
}
</style>
