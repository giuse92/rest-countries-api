<template>
  <div class="home">
    <b-row>
      <b-col md="7" class="d-flex justify-content-start align-items-center"
        ><SearchInput @onClickSearch="onClickSearchInput" class="mw-100"
      /></b-col>
      <b-col md="3"></b-col>
      <b-col md="2"
        ><SelectInput @onChangeSelect="onChangeSelectInput"
      /></b-col>
    </b-row>
    <div class="my-5">
      <div v-if="error.countriesInfo">Error</div>
      <div v-else>
        <div v-if="!isLoaded.countriesInfo">Loading...</div>
        <b-row v-else>
          <b-col md="3" :key="`${i}`" v-for="(country, i) of countriesToShow">
            <b-link :to="`/detail/${country.name.toLowerCase()}`">
              <b-card
                :title="country.name"
                :img-src="country.flag"
                :img-alt="country.name"
                img-top
                img-width="100%"
                tag="article"
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
import SearchInput from "../components/SearchInput.vue";
import SelectInput from "../components/SelectInput.vue";

export default {
  name: "Home",
  data() {
    return {
      isLoaded: {
        countriesInfo: false,
      },
      error: { countriesInfo: false },
      countriesInfo: [],
      countriesToShow: [],
    };
  },
  components: {
    SearchInput,
    SelectInput,
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
          this.countriesToShow = res.data;
          this.isLoaded.countriesInfo = true;
        })
        .catch((e) => {
          console.error(e);
          this.error.countriesInfo = true;
        });
    },
    onClickSearchInput(array) {
      this.countriesToShow = array;
    },
    onChangeSelectInput(selectedValue) {
      if (selectedValue !== "") {
        this.countriesToShow = this.countriesInfo.filter(
          (obj) => obj.region === selectedValue
        );
      } else {
        this.countriesToShow = this.countriesInfo;
      }
    },
  },
};
</script>
