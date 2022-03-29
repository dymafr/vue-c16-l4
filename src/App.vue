<template>
  <div class="p-20">
    <div class="mb-20 d-flex w100 justify-content-center align-items-center">
      <input
        v-model="input"
        @keydown.enter="addItem"
        type="text"
        class="flex-fill mr-20"
      />
      <button class="btn btn-primary mr-20" @click="addItem">Ajouter</button>
    </div>
    <div>
      <TransitionGroup tag="ul">
        <li
          class="w-100 card mb-10"
          v-for="(item, index) in items"
          @click="removeItem(index)"
        >
          {{ item }}
        </li>
      </TransitionGroup>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const input = ref('');
const items = ref<string[]>(['Pomme', 'Fraise', 'Poire']);

function addItem() {
  items.value.push(input.value);
  input.value = '';
}

function removeItem(index: number) {
  items.value.splice(index, 1);
}
</script>

<style lang="scss">
@import './assets/scss/base.scss';

li {
  cursor: pointer;
}

.v-enter-from {
  transform: translateX(30px);
  opacity: 0;
}

.v-enter-active {
  transition: all 1s;
}
</style>
