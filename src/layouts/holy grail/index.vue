<template>
  <div class="container">
    <header :style="{ 'background-color': titleBgColor }">
      <!-- Header content -->
      <slot name="header"></slot>
    </header>

    <nav :style="{ 'background-color': navBgColor }">
      <!-- Navigation -->
      <slot name="nav"></slot>
    </nav>

    <main>
      <!-- Main content -->
      <slot name="main"></slot>
    </main>

    <aside>
      <!-- Sidebar / Ads -->
      <slot name="aside"></slot>
    </aside>

    <footer>
      <!-- Footer content -->
      <slot name="footer"></slot>
    </footer>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  props: {
    titleBgColor: {
      type: String,
      default: "#3498db"
    },
    navBgColor: {
      type: String,
      default: "#f60"
    }
  }
});
</script>

<style lang="scss" scoped>
.container {
  display: grid;

  grid-template-areas:
    "header header header"
    "nav content side"
    "footer footer footer";

  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  grid-gap: 10px;

  height: 100vh;

  header {
    grid-area: header;
  }

  nav {
    grid-area: nav;
    margin-left: 0.5rem;
  }

  main {
    grid-area: content;
  }

  aside {
    grid-area: side;
    margin-right: 0.5rem;
  }

  footer {
    grid-area: footer;
  }
}
@media (max-width: 768px) {
  .container {
    grid-template-areas:
      "header"
      "nav"
      "content"
      "side"
      "footer";

    grid-template-columns: 1fr;
    grid-template-rows:
      auto /* Header */
      minmax(75px, auto) /* Nav */
      1fr /* Content */
      minmax(75px, auto) /* Sidebar */
      auto; /* Footer */
    nav,
    aside {
      margin: 0;
    }
  }
}
</style>
