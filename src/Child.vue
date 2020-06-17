<template>
  <div>
    <p>mouseX: {{ mouseX }}</p>
    <p>mouseY: {{ mouseY }}</p>
  </div>
</template>

<script>
import { useMousePosition } from "./mouse";
import { useStore } from "./MyStore";

export default {
  setup() {
    const testStore = useStore();
    const { x, y } = useMousePosition();
    let mouseX = x;
    let mouseY = y;

    return {
      mouseX,
      mouseY
    };
  }
};
</script>

<style scoped>
</style>
