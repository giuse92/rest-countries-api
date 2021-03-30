<template>
  <div class="d-flex align-items-center">
    <b-button><b-icon-search></b-icon-search></b-button>
    <b-form-input v-model="searchValue" type="search"></b-form-input>
  </div>
</template>

<script>
export default {
  name: "SearchInput",
  data() {
    return {
      searchValue: "",
    };
  },
};
</script>

<style>
div {
  margin: 0;
  padding: 0;
}
</style>
