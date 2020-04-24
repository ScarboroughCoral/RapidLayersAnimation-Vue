<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button type="button" @click="showModal">Open Modal!</button>
    <Model v-show="isModalVisible" @close="closeModal">
      <template slot="header">
        <h2>一起造轮子</h2>
      </template>
      <template slot="body">
        <p class="modal-body">重复制造它的意义有两个:</p>
        <ol>
          <li>你的到了锻炼</li>
          <li>你牛逼的话可以比前人造的更好，间接造福了全世界</li>
        </ol>
        <p
          class="modal-body"
        >重复制造轮子和重复发明轮子是不一样的。发明是researching，制造是engineering，不能混为一谈。我们说，不要重复发明轮子，但是没有说，不要重复制造轮子。</p>
        <p class="reference-name">——轮子哥</p>
      </template>
    </Model>
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
.modal-body::first-letter {
  font-size: 2em;
  color: #3498db;
}
.reference-name {
  text-align: end;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  li {
    display: inline-block;
    margin: 0 10px;
  }
}
a {
  color: #42b983;
}
</style>
