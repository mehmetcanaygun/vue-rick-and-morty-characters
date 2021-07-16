<template>
  <TheNavbar />
  <router-view />
</template>

<script>
import TheNavbar from "./components/TheNavbar";

export default {
  name: "App",
  components: {
    TheNavbar,
  },
};
</script>

<style lang="scss">
// Imports
@import "./styles/variables";

// Reset
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
}

ul {
  list-style-type: none;
}

a {
  text-decoration: none;
}
</style>
