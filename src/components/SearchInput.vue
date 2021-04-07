<template>
  <div>
    <b-input-group>
      <b-input-group-prepend>
        <b-button @click="getCountryByName" variant="light"
          ><b-icon-search></b-icon-search
        ></b-button>
      </b-input-group-prepend>
      <b-form-input
        v-model="searchValue"
        placeholder="Search for a country..."
        type="text"
        variant="light"
      ></b-form-input>
    </b-input-group>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "SearchInput",
  data() {
    return {
      error: false,
      isLoaded: false,
      searchValue: "",
      countryBySearch: [],
    };
  },
  methods: {
    getCountryByName() {
      axios
        .get("https://restcountries.eu/rest/v2/name/" + this.searchValue)
        .then((res) => {
          this.isLoaded = true;
          if (res.data.status) throw new Error(res.data.message);
          this.countryBySearch = res.data;
          let data = res.data;
          this.$emit("onClickSearch", data);
        })
        .catch((e) => {
          console.error(e);
          this.error = true;
        });
      this.searchValue = "";
    },
  },
};
</script>

<style>
div {
  margin: 0;
  padding: 0;
}
</style>
