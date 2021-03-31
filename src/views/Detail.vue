<template>
  <div>
    <router-link to="/"
      ><b-button
        ><b-icon-arrow-left></b-icon-arrow-left> Back</b-button
      ></router-link
    >
    <b-row class="mt-5">
      <b-col md="5">
        <b-img
          :src="countryInfo[0].flag"
          fluid
          :alt="countryInfo[0].name + ' flag'"
        ></b-img>
      </b-col>
      <b-col md="2"> </b-col>
      <b-col md="5">
        <h3>{{ countryInfo[0].name }}</h3>
        <p class="d-flex justify-content-between">
          <span
            ><strong>Native Name: </strong>{{ countryInfo[0].nativeName }}</span
          ><span
            ><strong>Top Level Domain: </strong
            >{{ countryInfo[0].topLevelDomain[0] }}</span
          >
        </p>
        <p class="d-flex justify-content-between">
          <span
            ><strong>Population: </strong>{{ countryInfo[0].population }}</span
          ><span
            ><strong>Currencies: </strong
            >{{ countryInfo[0].currencies[0].name }}</span
          >
        </p>
        <p class="d-flex justify-content-between">
          <span><strong>Region: </strong>{{ countryInfo[0].region }}</span
          ><span
            ><strong>Languages: </strong
            >{{ countryInfo[0].languages[0].name }}</span
          >
        </p>
        <p><strong>Subregion: </strong>{{ countryInfo[0].subregion }}</p>
        <p><strong>Capital: </strong>{{ countryInfo[0].capital }}</p>
        <div>
          <strong>Border Countries: </strong>
          <b-button
            v-for="(border, i) of countryInfo[0].borders"
            :key="`border-${i}`"
            >{{ border }}</b-button
          >
        </div>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Detail",
  data() {
    return {
      countryInfo: [],
    };
  },
  created() {
    axios
      .get(`https://restcountries.eu/rest/v2/name/${this.$route.params.name}`)
      .then((res) => {
        this.countryInfo = res.data;
      })
      .catch((e) => console.error(e));
  },
};
</script>
