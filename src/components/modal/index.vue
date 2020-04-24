<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div
        class="modal"
        role="dialog"
        :style="{'max-width':maxWidth}"
        aria-labelledby="modalTitle"
        aria-describedby="modalDescription"
      >
        <header class="modal-header" id="modalTitle">
          <slot name="header">This is the default tile!</slot>
          <button type="button" class="btn-close" @click="close" aria-label="Close modal">x</button>
        </header>
        <section class="modal-body" id="modalDescription">
          <slot name="body">I'm the default body!</slot>
        </section>
        <footer class="modal-footer">
          <slot name="footer">轮子是个好东西</slot>
          <button type="button" class="btn-green" @click="close" aria-label="Close modal">关闭</button>
        </footer>
      </div>
    </div>
  </transition>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "modal",
  props: {
    maxWidth: {
      type: String,
      default: "400px"
    }
  },
  methods: {
    close() {
      this.$emit("close");
    }
  }
});
</script>

<style lang="scss" scoped>
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
  .modal {
    background: #ffffff;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
    .modal-header,
    .modal-footer {
      padding: 15px;
      display: flex;
    }
    .modal-header {
      border-bottom: 1px solid #eeeeee;
      color: #4aae9b;
      justify-content: space-between;
      .btn-close {
        border: none;
        font-size: 20px;
        padding: 20px;
        cursor: pointer;
        font-weight: bold;
        color: #4aae9b;
        background: transparent;
      }
    }

    .modal-footer {
      border-top: 1px solid #eeeeee;
      justify-content: space-between;
      .btn-green {
        color: white;
        background: #4aae9b;
        border: 1px solid #4aae9b;
        border-radius: 2px;
      }
    }
    .modal-body {
      position: relative;
      padding: 20px 10px;
      justify-content: flex-start;
      text-align: start;
    }
  }
}
</style>
