<template>
    <transition name="loading-fade">
        <div class="loading-backdrop"></div>
    </transition>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
    props: {
        full: {
            type: Boolean,
            default: true,
        },
    },
});
</script>

<style scoped lang="scss">
.loading-fade-enter,
.loading-fade-leave-to {
    opacity: 0;
}
.loading-fade-enter-active {
    transition: opacity 10s;
}
.loading-backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.3);
}
</style>
