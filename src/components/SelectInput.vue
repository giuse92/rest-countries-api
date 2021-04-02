<template>
  <b-form-select
    v-model="selectForm.value"
    :options="selectForm.options"
    @change="filterByRegion"
  ></b-form-select>
</template>

<script>
//import axios from "axios";
export default {
  name: "SelectInput",
  data() {
    return {
      selectForm: {
        value: "",
        options: [
          {
            value: "",
            text: "Filter By Region",
          },
          {
            value: "Africa",
            text: "Africa",
          },
          {
            value: "Americas",
            text: "Americas",
          },
          { value: "Asia", text: "Asia" },
          { value: "Europe", text: "Europe" },
          { value: "Oceania", text: "Oceania" },
        ],
      },
    };
  },
  methods: {
    filterByRegion() {
      this.$emit("onChangeSelect", this.selectForm.value);
      /*if (this.selectForm.value === "") {
        return null;
      } else {
        axios
          .get(
            `https://restcountries.eu/rest/v2/region/${this.selectForm.value}`
          )
          .then((res) => {
            let data = res.data;
            this.$emit("onChangeSelect", data);
          })
          .catch((e) => console.error(e));
      }*/
    },
  },
};
</script>

<style></style>
