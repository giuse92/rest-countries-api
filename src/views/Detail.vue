<template>
  <div>
    <router-link to="/"
      ><b-button
        ><b-icon-arrow-left></b-icon-arrow-left> Back</b-button
      ></router-link
    >
    <p v-if="!isLoaded">Loading...</p>
    <b-row v-else class="mt-5">
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
        <div class="d-flex justify-content-between">
          <span><strong>Region: </strong>{{ countryInfo[0].region }}</span>
          <p>
            <strong>Languages: </strong
            ><span v-for="(country, i) of countryInfo[0].languages" :key="i"
              >{{ country.name }}
            </span>
          </p>
        </div>
        <p><strong>Subregion: </strong>{{ countryInfo[0].subregion }}</p>
        <p><strong>Capital: </strong>{{ countryInfo[0].capital }}</p>
        <div>
          <strong>Border Countries: </strong>
          <span v-if="countryInfo[0].borders.length === 0">No borders</span>
          <b-button
            v-for="(border, i) of countryInfo[0].borders"
            v-else
            class="m-1"
            :key="`border-${i}`"
            :to="`/detail/${countryName(border)}`"
            >{{ countryName(border) | capitalize }}</b-button
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
      isLoaded: false,
      countryInfo: [],
    };
  },
  created() {
    this.getDetail();
  },
  watch: {
    "$route.params.name": function () {
      this.getDetail();
      this.isLoaded = false;
    },
  },
  methods: {
    getDetail() {
      axios
        .get(
          `https://restcountries.eu/rest/v2/name/${this.$route.params.name}?fullText=true`
        )
        .then((res) => {
          this.isLoaded = true;
          this.countryInfo = res.data;
        })
        .catch((e) => console.error(e));
    },
    countryName(code) {
      switch (code) {
        case "AFG":
          code = "afghanistan";
          break;
        case "ALA":
          code = "åland islands";
          break;
        case "ALB":
          code = "albania";
          break;
        case "DZA":
          code = "algeria";
          break;
        case "ASM":
          code = "american samoa";
          break;
        case "AND":
          code = "andorra";
          break;
        case "AGO":
          code = "angola";
          break;
        case "AIA":
          code = "anguilla";
          break;
        case "ARG":
          code = "argentina";
          break;
        case "ATA":
          code = "antarctica";
          break;
        case "ATG":
          code = "antigua and barbuda";
          break;
        case "ARM":
          code = "armenia";
          break;
        case "ABW":
          code = "aruba";
          break;
        case "AUS":
          code = "australia";
          break;
        case "AUT":
          code = "austria";
          break;
        case "AZE":
          code = "azerbaijan";
          break;
        case "BHS":
          code = "bahamas";
          break;
        case "BHR":
          code = "bahrain";
          break;
        case "BGD":
          code = "bangladesh";
          break;
        case "BRB":
          code = "barbados";
          break;
        case "BLR":
          code = "belarus";
          break;
        case "BEL":
          code = "belgium";
          break;
        case "BLZ":
          code = "belize";
          break;
        case "BEN":
          code = "benin";
          break;
        case "BMU":
          code = "bermuda";
          break;
        case "BTN":
          code = "bhutan";
          break;
        case "BOL":
          code = "bolivia (plurinational state of)";
          break;
        case "BES":
          code = "bonaire, sint eustatius and saba";
          break;
        case "BIH":
          code = "bosnia and herzegovina";
          break;
        case "BWA":
          code = "botswana";
          break;
        case "BVT":
          code = "bouvet island";
          break;
        case "BRA":
          code = "brazil";
          break;
        case "IOT":
          code = "british indian ocean territory";
          break;
        case "UMI":
          code = "united states minor outlying islands";
          break;
        case "VGB":
          code = "virgin islands (british)";
          break;
        case "VIR":
          code = "virgin islands (u.s.)";
          break;
        case "BRN":
          code = "brunei darussalam";
          break;
        case "BGR":
          code = "bulgaria";
          break;
        case "BFA":
          code = "burkina faso";
          break;
        case "BDI":
          code = "burundi";
          break;
        case "KHM":
          code = "cambodia";
          break;
        case "CMR":
          code = "cameroon";
          break;
        case "CAN":
          code = "canada";
          break;
        case "CPV":
          code = "cabo verde";
          break;
        case "CYM":
          code = "cayman islands";
          break;
        case "CAF":
          code = "central african republic";
          break;
        case "TCD":
          code = "chad";
          break;
        case "CHL":
          code = "chile";
          break;
        case "CHN":
          code = "china";
          break;
        case "CXR":
          code = "christmas island";
          break;
        case "CCK":
          code = "cocos (keeling) islands";
          break;
        case "COL":
          code = "colombia";
          break;
        case "COM":
          code = "comoros";
          break;
        case "COG":
          code = "congo";
          break;
        case "COD":
          code = "congo (democratic republic of the)";
          break;
        case "COK":
          code = "cook islands";
          break;
        case "CRI":
          code = "costa rica";
          break;
        case "HRV":
          code = "croatia";
          break;
        case "CUB":
          code = "cuba";
          break;
        case "CUW":
          code = "curaçao";
          break;
        case "CYP":
          code = "cyprus";
          break;
        case "CZE":
          code = "czech republic";
          break;
        case "DNK":
          code = "denmark";
          break;
        case "DJI":
          code = "djibouti";
          break;
        case "DMA":
          code = "dominica";
          break;
        case "DOM":
          code = "dominican republic";
          break;
        case "ECU":
          code = "ecuador";
          break;
        case "EGY":
          code = "egypt";
          break;
        case "SLV":
          code = "el salvador";
          break;
        case "GNQ":
          code = "equatorial guinea";
          break;
        case "ERI":
          code = "eritrea";
          break;
        case "EST":
          code = "estonia";
          break;
        case "ETH":
          code = "ethiopia";
          break;
        case "FLK":
          code = "falkland islands (malvinas)";
          break;
        case "FRO":
          code = "faroe islands";
          break;
        case "FJI":
          code = "fiji";
          break;
        case "FIN":
          code = "finland";
          break;
        case "FRA":
          code = "france";
          break;
        case "GUF":
          code = "french guiana";
          break;
        case "PYF":
          code = "french polynesia";
          break;
        case "ATF":
          code = "french southern territories";
          break;
        case "GAB":
          code = "gabon";
          break;
        case "GMB":
          code = "gambia";
          break;
        case "GEO":
          code = "georgia";
          break;
        case "DEU":
          code = "germany";
          break;
        case "GHA":
          code = "ghana";
          break;
        case "GIB":
          code = "gibraltar";
          break;
        case "GRC":
          code = "greece";
          break;
        case "GRL":
          code = "greenland";
          break;
        case "GRD":
          code = "grenada";
          break;
        case "GLP":
          code = "guadeloupe";
          break;
        case "GUM":
          code = "guam";
          break;
        case "GTM":
          code = "guatemala";
          break;
        case "GGY":
          code = "guernsey";
          break;
        case "GIN":
          code = "guinea";
          break;
        case "GNB":
          code = "guinea-bissau";
          break;
        case "GUY":
          code = "guyana";
          break;
        case "HTI":
          code = "haiti";
          break;
        case "HMD":
          code = "heard island and mcdonald islands";
          break;
        case "VAT":
          code = "holy see";
          break;
        case "HND":
          code = "honduras";
          break;
        case "HKG":
          code = "hong kong";
          break;
        case "HUN":
          code = "hungary";
          break;
        case "ISL":
          code = "iceland";
          break;
        case "IND":
          code = "india";
          break;
        case "IDN":
          code = "indonesia";
          break;
        case "CIV":
          code = "côte d'ivoire";
          break;
        case "IRN":
          code = "iran (islamic republic of)";
          break;
        case "IRQ":
          code = "iraq";
          break;
        case "IRL":
          code = "ireland";
          break;
        case "IMN":
          code = "isle of man";
          break;
        case "ISR":
          code = "israel";
          break;
        case "ITA":
          code = "italy";
          break;
        case "JAM":
          code = "jamaica";
          break;
        case "JPN":
          code = "japan";
          break;
        case "JEY":
          code = "jersey";
          break;
        case "JOR":
          code = "jordan";
          break;
        case "KAZ":
          code = "kazakhstan";
          break;
        case "KEN":
          code = "kenya";
          break;
        case "KIR":
          code = "kiribati";
          break;
        case "KWT":
          code = "kuwait";
          break;
        case "KGZ":
          code = "kyrgyzstan";
          break;
        case "LAO":
          code = "lao people's democratic republic";
          break;
        case "LVA":
          code = "latvia";
          break;
        case "LBN":
          code = "lebanon";
          break;
        case "LSO":
          code = "lesotho";
          break;
        case "LBR":
          code = "liberia";
          break;
        case "LBY":
          code = "libya";
          break;
        case "LIE":
          code = "liechtenstein";
          break;
        case "LTU":
          code = "lithuania";
          break;
        case "LUX":
          code = "luxembourg";
          break;
        case "MAC":
          code = "macao";
          break;
        case "MKD":
          code = "macedonia (the former yugoslav republic of)";
          break;
        case "MDG":
          code = "madagascar";
          break;
        case "MWI":
          code = "malawi";
          break;
        case "MYS":
          code = "malaysia";
          break;
        case "MDV":
          code = "maldives";
          break;
        case "MLI":
          code = "mali";
          break;
        case "MLT":
          code = "malta";
          break;
        case "MHL":
          code = "marshall islands";
          break;
        case "MTQ":
          code = "martinique";
          break;
        case "MRT":
          code = "mauritania";
          break;
        case "MUS":
          code = "mauritius";
          break;
        case "MYT":
          code = "mayotte";
          break;
        case "MEX":
          code = "mexico";
          break;
        case "FSM":
          code = "micronesia (federated states of)";
          break;
        case "MDA":
          code = "moldova (republic of)";
          break;
        case "MCO":
          code = "monaco";
          break;
        case "MNG":
          code = "mongolia";
          break;
        case "MNE":
          code = "montenegro";
          break;
        case "MSR":
          code = "montserrat";
          break;
        case "MAR":
          code = "morocco";
          break;
        case "MOZ":
          code = "mozambique";
          break;
        case "MMR":
          code = "myanmar";
          break;
        case "NAM":
          code = "namibia";
          break;
        case "NRU":
          code = "nauru";
          break;
        case "NPL":
          code = "nepal";
          break;
        case "NLD":
          code = "netherlands";
          break;
        case "NCL":
          code = "new caledonia";
          break;
        case "NZL":
          code = "new zealand";
          break;
        case "NIC":
          code = "nicaragua";
          break;
        case "NER":
          code = "niger";
          break;
        case "NGA":
          code = "nigeria";
          break;
        case "NIU":
          code = "niue";
          break;
        case "NFK":
          code = "norfolk island";
          break;
        case "PRK":
          code = "korea (democratic people's republic of)";
          break;
        case "MNP":
          code = "northern mariana islands";
          break;
        case "NOR":
          code = "norway";
          break;
        case "OMN":
          code = "oman";
          break;
        case "PAK":
          code = "pakistan";
          break;
        case "PLW":
          code = "palau";
          break;
        case "PSE":
          code = "palestine, state of";
          break;
        case "PAN":
          code = "panama";
          break;
        case "PNG":
          code = "papua new guinea";
          break;
        case "PRY":
          code = "paraguay";
          break;
        case "PER":
          code = "peru";
          break;
        case "PHL":
          code = "philippines";
          break;
        case "PCN":
          code = "pitcairn";
          break;
        case "POL":
          code = "poland";
          break;
        case "PRT":
          code = "portugal";
          break;
        case "PRI":
          code = "puerto rico";
          break;
        case "QAT":
          code = "qatar";
          break;
        case "KOS":
          code = "republic of kosovo";
          break;
        case "REU":
          code = "réunion";
          break;
        case "ROU":
          code = "romania";
          break;
        case "RUS":
          code = "russian federation";
          break;
        case "RWA":
          code = "rwanda";
          break;
        case "BLM":
          code = "saint barthélemy";
          break;
        case "SHN":
          code = "saint helena, ascension and tristan da cunha";
          break;
        case "KNA":
          code = "saint kitts and nevis";
          break;
        case "LCA":
          code = "saint lucia";
          break;
        case "MAF":
          code = "saint martin (french part)";
          break;
        case "SPM":
          code = "saint pierre and miquelon";
          break;
        case "VCT":
          code = "saint vincent and the grenadines";
          break;
        case "WSM":
          code = "samoa";
          break;
        case "SMR":
          code = "san marino";
          break;
        case "STP":
          code = "sao tome and principe";
          break;
        case "SAU":
          code = "saudi arabia";
          break;
        case "SEN":
          code = "senegal";
          break;
        case "SRB":
          code = "serbia";
          break;
        case "SYC":
          code = "seychelles";
          break;
        case "SLE":
          code = "sierra leone";
          break;
        case "SGP":
          code = "singapore";
          break;
        case "SXM":
          code = "sint maarten (dutch part)";
          break;
        case "SVK":
          code = "slovakia";
          break;
        case "SVN":
          code = "slovenia";
          break;
        case "SLB":
          code = "solomon islands";
          break;
        case "SOM":
          code = "somalia";
          break;
        case "ZAF":
          code = "south africa";
          break;
        case "SGS":
          code = "south georgia and the south sandwich islands";
          break;
        case "KOR":
          code = "korea (republic of)";
          break;
        case "SSD":
          code = "south sudan";
          break;
        case "ESP":
          code = "spain";
          break;
        case "LKA":
          code = "sri lanka";
          break;
        case "SDN":
          code = "sudan";
          break;
        case "SUR":
          code = "suriname";
          break;
        case "SJM":
          code = "svalbard and jan mayen";
          break;
        case "SWZ":
          code = "swaziland";
          break;
        case "SWE":
          code = "sweden";
          break;
        case "CHE":
          code = "switzerland";
          break;
        case "SYR":
          code = "syrian arab republic";
          break;
        case "TWN":
          code = "taiwan";
          break;
        case "TJK":
          code = "tajikistan";
          break;
        case "TZA":
          code = "tanzania, united republic of";
          break;
        case "THA":
          code = "thailand";
          break;
        case "TLS":
          code = "timor-leste";
          break;
        case "TGO":
          code = "togo";
          break;
        case "TKL":
          code = "tokelau";
          break;
        case "TON":
          code = "tonga";
          break;
        case "TTO":
          code = "trinidad and tobago";
          break;
        case "TUN":
          code = "tunisia";
          break;
        case "TUR":
          code = "turkey";
          break;
        case "TKM":
          code = "turkmenistan";
          break;
        case "TCA":
          code = "turks and caicos islands";
          break;
        case "TUV":
          code = "tuvalu";
          break;
        case "UGA":
          code = "uganda";
          break;
        case "UKR":
          code = "ukraine";
          break;
        case "ARE":
          code = "united arab emirates";
          break;
        case "GBR":
          code = "united kingdom of great britain and northern ireland";
          break;
        case "USA":
          code = "united states of america";
          break;
        case "URY":
          code = "uruguay";
          break;
        case "UZB":
          code = "uzbekistan";
          break;
        case "VUT":
          code = "vanuatu";
          break;
        case "VEN":
          code = "venezuela (bolivarian republic of)";
          break;
        case "VNM":
          code = "viet nam";
          break;
        case "WLF":
          code = "wallis and futuna";
          break;
        case "ESH":
          code = "western sahara";
          break;
        case "YEM":
          code = "yemen";
          break;
        case "ZMB":
          code = "zambia";
          break;
        case "ZWE":
          code = "zimbabwe";
          break;
        default:
          code;
          break;
      }
      return code;
    },
  },
  filters: {
    capitalize: function (value) {
      return value[0].toUpperCase() + value.slice(1);
    },
  },
};
</script>
