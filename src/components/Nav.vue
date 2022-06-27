<template>
  <nav>
    <p class="nav-title">Quiz Application</p>
  </nav>
</template>

<script>
export default {
  name: "Nav",
};
</script>

<style scoped>
nav {
  position: fixed;
  display: flex;
  align-items: center;
  width: 100vw;
  height: 50px;
  background-color: #860707;
  color: white;
  z-index: 2;
}

.nav-title {
  font-size: 1.3em;
  margin-left: 30px;
}

/* tablet */
@media screen and (max-width: 1024px) {
  .nav-title {
    margin-left: 50px;
  }
}
</style>
