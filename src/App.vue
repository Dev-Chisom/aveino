<template>
  <div>
    <Header />
    <Navbar />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Navbar from './components/Navbar.vue';

export default {
  name: 'App',
  components: {
    Header,
    Navbar,
  },
};
</script>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  min-height: 100vh;
  background: linear-gradient(90deg, #bd0f4d 50%, #cb2964 50%) no-repeat center
    center/cover;
  font-family: 'Nunito', sans-serif;
  color: #fff;
  overflow: hidden;
}
</style>
