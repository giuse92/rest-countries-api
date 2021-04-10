<template>
  <div id="app">
    <b-navbar class="my-2 p-0">
      <b-container>
        <b-navbar-brand tag="h1" class="font-weight-bold"
          >Where in the world?</b-navbar-brand
        >
      </b-container>
    </b-navbar>
    <b-container>
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
}
</style>
