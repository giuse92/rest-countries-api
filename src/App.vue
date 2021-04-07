<template>
  <div id="app">
    <b-container>
      <b-navbar class="mb-4">
        <b-navbar-brand tag="h1" class="mb-0"
          >Where in the world?</b-navbar-brand
        >
      </b-navbar>
      <router-view />
    </b-container>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@300;800&display=swap");

#app {
  font-family: "Nunito Sans", sans-serif;
  height: 100vh;
}
</style>
