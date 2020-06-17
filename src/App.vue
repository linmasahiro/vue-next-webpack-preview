<template>
  <div>
    <img src="./logo.png" />
    <h1>Hello Vue 3!</h1>
    <button @click="inc">Clicked {{ state.count }} times.</button>
    <p>count: {{ state.count }}</p>
    <p>double: {{ state.double }}</p>
    <p>count1: {{ count1 }}</p>
    <p>count2: {{ count2 }}</p>
    <child-component />
  </div>
</template>

<script lang="ts">
import { ref, reactive, computed } from "vue";
import { provideStore } from "./MyStore";
import Child from "./Child.vue";

export default {
  components: {
    'child-component': Child
  },
  setup() {
    provideStore(ref([1, 2, 3]))
    const state = reactive({
      count: 0,
      double: computed(() => state.count * 2)
    });

    let count1 = ref(0);
    let count2 = 0;
    const inc = () => {
      count1.value++;
      count2++;
      state.count++;
    };

    return {
      state,
      count1,
      count2,
      inc
    };
  }
};
</script>

<style scoped>
img {
  width: 200px;
}
h1 {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
