<script setup>
import { ref } from 'vue';

import IconForward from '~icons/material-symbols/arrow-forward-ios-rounded';

const pageTop = ref(0);

function handleScroll() {
  pageTop.value = window.visualViewport.pageTop;
}

window.addEventListener('scroll', handleScroll);

function scrollToTop() {
  window.scrollTo(0, 0);
}
</script>

<template>
  <button class="scroll-to-top" @click="scrollToTop" v-if="pageTop > 250">
    <IconForward class="arrow-rotated" />
  </button>
</template>

<style scoped lang="scss">
.scroll-to-top {
  cursor: pointer;
  position: fixed;
  bottom: 3rem;
  right: 2rem;
  width: 4rem;
  height: 4rem;
  background: white;
  border: none;
  border-radius: 4px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  .arrow-rotated {
    transform: rotate(-90deg);
    color: black;
    font-size: 1.5rem;
  }
}
</style>
