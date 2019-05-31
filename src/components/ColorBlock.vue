<template>
  <div :style="{'background-color':colorCode}">
    <h1 @click="saveToLocalStorage">{{ colorCode }}</h1>
  </div>
</template>

<script>
export default {
  name: "ColorBlock",
  props: ["colorBlockId"],
  methods: {
    saveToLocalStorage() {
      console.log(this.colorBlockId);
      localStorage.setItem(
        `position ${this.colorBlockId}`,
        JSON.stringify(this.colorCode)
      );
    }
  },
  data() {
    let colorCode = "";

    // check local storage for locked code
    let localStorageCheck = JSON.parse(
      localStorage.getItem(`position ${this.colorBlockId}`)
    );

    if (localStorageCheck) {
      // assign color code if there is one based on position
      colorCode = localStorageCheck;
      console.log(localStorageCheck);
    } else {
      // generate random hex code
      colorCode =
        "#" +
        Math.random()
          .toString(16)
          .substring(3, 9);
    }
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
