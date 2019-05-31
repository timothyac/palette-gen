<template>
  <div class="grid-template">
    <ColorBlock/>
    <ColorBlock/>
    <ColorBlock/>
    <ColorBlock/>
  </div>
</template>

<script>
import ColorBlock from "./ColorBlock.vue";

export default {
  name: "Grid",
  components: {
    ColorBlock
  },
  methods: {}
};
</script>

<style scoped>
.grid-template {
  background: #555;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  height: 95vh;
}

@media (max-width: 800px) {
  .grid-template {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 500px) {
  .grid-template {
    grid-template-columns: 1fr;
  }
}
</style>