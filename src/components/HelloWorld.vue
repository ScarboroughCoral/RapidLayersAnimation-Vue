<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button type="button" @click="showModal">Open Modal!</button>
    <Model v-show="isModalVisible" @close="closeModal" />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Model from "./modal/index.vue";

@Component({
  components: {
    Model
  }
})
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;

  private isModalVisible = false;
  showModal() {
    this.isModalVisible = true;
  }
  closeModal() {
    this.isModalVisible = false;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
