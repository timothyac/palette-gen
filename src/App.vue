<template>
  <div id="app">
    <Header/>
    <Grid/>
    <Footer/>
  </div>
</template>

<script>
import Grid from "./components/Grid.vue";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "app",
  components: {
    Grid,
    Footer,
    Header
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
  font-family: Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
