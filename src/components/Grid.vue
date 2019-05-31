<template>
  <div class="grid-template">
    <ColorBlock v-bind:colorBlockId="1"/>
    <ColorBlock v-bind:colorBlockId="2"/>
    <ColorBlock v-bind:colorBlockId="3"/>
    <ColorBlock v-bind:colorBlockId="4"/>
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