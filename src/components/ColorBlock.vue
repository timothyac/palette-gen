<template>
  <div :style="{'background-color':colorCode}">
    <h1 @click="checkLocalStorage" v-bind:class="[isLocked?'locked':'unlocked']">{{ colorCode }}</h1>
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
        this.isLocked = false;
      } else {
        localStorage.setItem(
          `position ${this.colorBlockId}`,
          JSON.stringify(this.colorCode)
        );
        this.isLocked = true;
      }

      return;
    }
  },
  data: function() {
    let colorCode = "";
    let isLocked = null;

    // check local storage to see if anything is in there on load
    let localStorageCheck = JSON.parse(
      localStorage.getItem(`position ${this.colorBlockId}`)
    );

    if (localStorageCheck && localStorageCheck != "") {
      // assign color code if there is one based on position
      colorCode = localStorageCheck;
      console.log(localStorageCheck);
      isLocked = true;
    } else {
      // generate random hex code
      colorCode =
        "#" +
        Math.random()
          .toString(16)
          .substring(3, 9);
      isLocked = false;
    }
    return { colorCode, isLocked };
  }
};
</script>

<style scoped>
div {
  position: relative;
  height: 100%;
}

h1.unlocked {
  position: absolute;
  top: 50%;
  left: 35%;
  width: auto;
  color: whitesmoke;
}

h1.locked {
  position: absolute;
  top: 50%;
  left: 35%;
  width: auto;
  color: black;
}
</style>
