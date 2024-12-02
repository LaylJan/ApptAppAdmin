<template>
  <Navbar />
  <LandingPage />
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Navbar from './components/Navbar.vue';
import LandingPage from './components/LandingPage.vue';

export default {
  name: "App",
  components: {
    LandingPage,
    Navbar
  },
};
</script>

<style>

</style>
