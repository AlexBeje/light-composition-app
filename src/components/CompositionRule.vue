<script setup>
import { ref } from 'vue';
import IconForward from '~icons/material-symbols/arrow-forward-ios-rounded';

defineProps({
  id: Number,
  description: String,
  exampleImageNumber: Number,
});

const itemOpened = ref(false);

function toggleItem() {
  itemOpened.value = !itemOpened.value;
}
</script>

<template>
  <div class="container">
    <div class="top-section" @click="toggleItem">
      <img class="image" :src="'/images/' + id + '.jpeg'" />
    </div>
    <div class="bottom-section" v-if="itemOpened">
      <div class="subtitle mb-1">
        <h3 class="m-0">Ejemplo{{ exampleImageNumber > 1 ? 's' : '' }}</h3>
        <span class="horizontal-line" />
      </div>
      <img
        class="large-image mb-1"
        :src="'/images/' + id + '.' + index + '.jpeg'"
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
  border-radius: 8px;
  overflow: hidden;
  .top-section {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #1c1c1e;
    padding: 1rem;
    cursor: pointer;
    .image {
      width: 100%;
      background: #39383d;
      background-size: auto;
      object-fit: cover;
    }
    .title {
      flex: 1;
      margin: 0 1rem;
      font-weight: 500;
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
