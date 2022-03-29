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
      <ul>
        <li class="w-100 card mb-10" v-for="item in items">{{ item }}</li>
      </ul>
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
</script>

<style lang="scss">
@import './assets/scss/base.scss';

.fadeRight-leave-to {
  transform: translateX(10px);
  opacity: 0;
}

.fadeRight-enter-active,
.fadeRight-leave-active {
  transition: all 0.4s;
}

.fadeRight-enter-from {
  transform: translateX(-10px);
  opacity: 0;
}
</style>
