<template>
  <nav>
    <a href="#">home</a>
    <a href="#">about</a>
    <img src="../assets/images/girl.png" alt="face model" />
    <a href="#">gallery</a>
    <a href="#">contact</a>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
};
</script>

<style scoped>
nav {
  display: flex;
  justify-content: center;
  align-items: center;
}
nav a {
  display: inline-block;
  text-decoration: none;
  margin-right: 2em;
  font-weight: 300;
  text-transform: uppercase;
  color: #fff;
}
nav a:last-child {
  margin-right: 0;
}

@media screen and (max-width: 764px) {
  nav {
    flex-direction: column;
    margin-top: 1rem;
  }
  nav a {
    margin-right: 0;
    text-align: center !important;
    padding-bottom: 1rem;
  }
}
</style>
