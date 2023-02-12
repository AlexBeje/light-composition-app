<script setup>
import { ref } from 'vue';
import IconForward from '~icons/material-symbols/arrow-forward-ios-rounded';

defineProps({
  id: Number,
  description: String,
  title: String,
  exampleImageNumber: Number,
  horizontalAxis: Boolean,
});

const itemOpened = ref(false);

function toggleItem() {
  itemOpened.value = !itemOpened.value;
}
</script>

<template>
  <div class="container">
    <div class="top-section" @click="toggleItem">
      <img
        class="image"
        :src="
          '/images/' +
          (horizontalAxis ? 'horizontalAxis/' : 'verticalAxis/') +
          id +
          '.jpeg'
        "
      />
      <h1>{{ title }}</h1>
    </div>
    <div class="bottom-section" v-if="itemOpened">
      <div class="subtitle mb-1">
        <h3 class="m-0">Ejemplo{{ exampleImageNumber > 1 ? 's' : '' }}</h3>
        <span class="horizontal-line" />
      </div>
      <img
        class="large-image mb-1"
        :src="
          '/images/' +
          (horizontalAxis ? 'horizontalAxis/' : 'verticalAxis/') +
          id +
          '.' +
          index +
          '.jpeg'
        "
        v-for="index in exampleImageNumber"
        :key="index"
      />
      <div class="subtitle mb-1">
        <h3 class="m-0">Descripción</h3>
        <span class="horizontal-line" />
      </div>
      <span v-html="description" />
    </div>
  </div>
</template>

<style scoped lang="scss">
.subtitle {
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
  h3 {
    display: inline;
  }
  .horizontal-line {
    background: rgba(255, 255, 255, 0.87);
    height: 1px;
    width: 100%;
  }
}
.m-0 {
  margin: 0;
}
.mb-1 {
  margin-bottom: 1rem;
}
.container {
  overflow: hidden;
  .top-section {
    background: white;
    color: black;
    cursor: pointer;
    padding: 1rem;
    text-align: center;
    h1 {
      margin: 0.5rem 0 0 0;
    }
    .image {
      width: 100%;
    }
  }
  .bottom-section {
    padding: 1rem;
    display: flex;
    flex-direction: column;
    background: linear-gradient(
      180deg,
      rgb(18, 18, 18) 0%,
      rgba(28, 28, 28, 1) 100%
    );
  }
}
</style>
