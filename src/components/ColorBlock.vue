<template>
  <div :style="{'background-color':colorCode}">
    <h1>{{ colorCode }}</h1>
  </div>
</template>

<script>
export default {
  name: "ColorBlock",
  methods: {},
  data() {
    // generate random hex code
    let colorCode =
      "#" +
      Math.random()
        .toString(16)
        .substring(3, 9);
    return { colorCode };
  }
};
</script>

<style scoped>
div {
  position: relative;
  height: 100%;
}

h1 {
  position: absolute;
  top: 50%;
  left: 35%;
  width: auto;
  color: whitesmoke;
  -webkit-text-stroke: 0.5px black;
}
</style>
