<template>
  <div :style="{'background-color':colorCode}">
    <h1 @click="checkLocalStorage">{{ colorCode }}</h1>
  </div>
</template>

<script>
export default {
  name: "ColorBlock",
  props: ["colorBlockId"],
  methods: {
    checkLocalStorage() {
      // check local storage to determine whether to delete or add
      let localStorageCheck = JSON.parse(
        localStorage.getItem(`position ${this.colorBlockId}`)
      );

      // if  true, it will delete previous storage, if not it will add
      if (localStorageCheck && localStorageCheck != "") {
        localStorage.removeItem(`position ${this.colorBlockId}`);
      } else {
        localStorage.setItem(
          `position ${this.colorBlockId}`,
          JSON.stringify(this.colorCode)
        );
      }

      return;
    }
  },
  data() {
    let colorCode = "";

    // check local storage to see if anything is in there on load
    let localStorageCheck = JSON.parse(
      localStorage.getItem(`position ${this.colorBlockId}`)
    );

    if (localStorageCheck && localStorageCheck != "") {
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
