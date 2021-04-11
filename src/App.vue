<template>
  <div>
    <router-link to="/"><NavBar /></router-link>
    <router-view />
  </div>
</template>

<script>
import NavBar from "./components/NavBar";
export default {
  components: {
    NavBar,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Kumbh+Sans:wght@400;700&display=swap");
body {
  font-weight: 400;
}

#app {
  font-family: "Kumbh Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h1,
h2,
h3,
h4,
h5 {
  font-weight: 700;
}
</style>
