<script setup>
import { ref } from 'vue';
import CompositionRule from './components/CompositionRule.vue';
import ScrollToTop from './components/ScrollToTop.vue';
import horizontalAxisData from './data/horizontalAxisData.json';
import verticalAxisData from './data/verticalAxisData.json';
import PhotoCamera from '~icons/material-symbols/photo-camera';

const horizontalAxis = ref(true);

const toggleAxis = () => {
  horizontalAxis.value = !horizontalAxis.value;
};
</script>

<template>
  <div class="app-container">
    <div class="title">
      <h1>Eje Horizontal</h1>
      <PhotoCamera class="icon" v-if="horizontalAxis" @click="toggleAxis" />
      <PhotoCamera class="icon icon--active" v-else @click="toggleAxis" />
    </div>
    <div class="composition-rules" v-if="horizontalAxis">
      <CompositionRule
        v-for="{ id, description, exampleImageNumber, title } in horizontalAxisData"
        :id="id"
        :description="description"
        :key="id"
        :title="title"
        :exampleImageNumber="exampleImageNumber"
        :horizontalAxis="horizontalAxis"
      />
    </div>
    <div class="composition-rules" v-else>
      <CompositionRule
        v-for="{ id, description, exampleImageNumber, title } in verticalAxisData"
        :id="id"
        :description="description"
        :key="id"
        :title="title"
        :exampleImageNumber="exampleImageNumber"
        :horizontalAxis="horizontalAxis"
      />
    </div>
    <ScrollToTop />
  </div>
</template>

<style scoped lang="scss">
h1 {
  font-weight: 700;
  margin: 0;
}
.title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 2rem 0 1rem 0;
}
.app-container {
  margin: 1rem 1rem 3rem 1rem;
}
.composition-rules {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.icon {
  width: 32px;
  height: 32px;
  &--active {
    color: #DFD1C2;
  }
}
</style>
