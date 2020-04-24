<template>
  <div id="app">
    <Holy>
      <template v-slot:header>
        <h1>一起造轮子</h1>
      </template>
      <template v-slot:nav>
        <router-link to="/">Home</router-link>|
        <router-link to="/about">About</router-link>
      </template>

      <template v-slot:main>
        <router-view />
      </template>
    </Holy>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import Holy from "@/layouts/holy grail/index.vue";
export default Vue.extend({
  components: {
    Holy
  }
});
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
