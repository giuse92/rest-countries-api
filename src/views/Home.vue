<template>
  <div class="home">
    <b-row>
      <b-col md="4" class="d-flex justify-content-center align-items-center"
        ><b-icon-search class="mr-1"></b-icon-search
        ><b-form-input v-model="searchValue" type="search"></b-form-input
      ></b-col>
      <b-col md="6"></b-col>
      <b-col md="2"
        ><b-form-select
          v-model="selectForm.value"
          :options="selectForm.options"
        ></b-form-select
      ></b-col>
    </b-row>
    <div class="my-5">
      <div v-if="error.countriesInfo">Error</div>
      <div v-else>
        <div v-if="!isLoaded.countriesInfo">Loading...</div>
        <b-row v-else>
          <b-col md="3" :key="`${i}`" v-for="(country, i) of countriesInfo">
            <b-link :to="`/detail/${country.name.toLowerCase()}`">
              <b-card
                :title="country.name"
                :img-src="country.flag"
                :img-alt="country.name"
                img-top
                img-width="100%"
                tag="div"
                class="mb-2"
              >
                <b-card-text
                  ><strong>Population:</strong
                  >{{ country.population }}</b-card-text
                >
                <b-card-text
                  ><strong>Region:</strong>{{ country.region }}</b-card-text
                >
                <b-card-text
                  ><strong>Capital:</strong>{{ country.capital }}</b-card-text
                >
              </b-card>
            </b-link>
          </b-col>
        </b-row>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      isLoaded: {
        countriesInfo: false,
      },
      error: { countriesInfo: false },
      countriesInfo: [],
      searchValue: "",
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
  created() {
    this.getAllCountriesInfo("https://restcountries.eu/rest/v2/all");
  },
  methods: {
    getAllCountriesInfo(apiUrl) {
      axios
        .get(apiUrl)
        .then((res) => {
          this.countriesInfo = res.data;
          this.isLoaded.countriesInfo = true;
        })
        .catch((e) => {
          console.error(e);
          this.error.countriesInfo = true;
        });
    },
  },
};
</script>
