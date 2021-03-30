<template>
  <b-form-select
    v-model="selectForm.value"
    :options="selectForm.options"
  ></b-form-select>
</template>

<script>
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
            value: "africa",
            text: "Africa",
          },
          {
            value: "america",
            text: "America",
          },
          { value: "asia", text: "Asia" },
          { value: "europe", text: "Europe" },
          { value: "oceania", text: "Oceania" },
        ],
      },
    };
  },
};
</script>

<style></style>
