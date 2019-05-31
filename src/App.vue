<template>
  <div id="app">
    <Grid/>
    <Footer/>
  </div>
</template>

<script>
import Grid from "./components/Grid.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "app",
  components: {
    Grid,
    Footer
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
