<template>
  <div id="app" :style="themeLight ? themeLightStyle : themeDarkStyle">
    <b-container>
      <b-navbar class="d-flex" :type="themeLight ? 'light' : 'dark'">
        <b-navbar-brand tag="h1" class="mb-0"
          >Where in the world?</b-navbar-brand
        >
        <b-button :variant="themeLight ? 'light' : 'dark'" @click="toggleTheme"
          ><b-icon-moon></b-icon-moon>
          {{ themeLight ? "Light" : "Dark" }} Mode</b-button
        >
      </b-navbar>
      <router-view />
    </b-container>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      themeLight: true,
      themeLightStyle: {
        backgroundColor: "hsl(0, 0%, 98%)",
        color: "hsl(200, 15%, 8%)",
      },
      themeDarkStyle: {
        backgroundColor: "hsl(207, 26%, 17%)",
        color: "hsl(0, 0%, 100%)",
      },
    };
  },
  methods: {
    toggleTheme() {
      this.themeLight = !this.themeLight;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@300;800&display=swap");

#app {
  font-family: "Nunito Sans", sans-serif;
  height: 100vh;
}
</style>
