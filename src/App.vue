<template>
  <div id="app">
    <MyDropdown :options="cities" v-model="cityIndex"></MyDropdown>
    <MyDropdown :options="areas" v-model="areaIndex"></MyDropdown>
    <span>{{ zip }}</span>
  </div>
</template>

<script>
import axios from "axios";
import _ from "lodash";
import MyDropdown from "@/components/MyDropdown";

export default {
  name: "app",

  components: {
    MyDropdown
  },

  data() {
    return {
      cities: [],
      cityIndex: 0,
      areaIndex: 0
    };
  },

  mounted() {
    axios
      .get("http://localhost:8081/api")
      .then(response => (this.cities = response.data))
      .catch(e => console.log(e));
  },

  computed: {
    areas() {
      if (_.isEmpty(this.cities)) {
        return [];
      }

      return this.cities[this.cityIndex].areas;
    },

    zip() {
      if (_.isEmpty(this.areas)) {
        return [];
      }

      return this.areas[this.areaIndex].zip;
    }
  },

  watch: {
    cityIndex() {
      this.areaIndex = 0;
    }
  }
};
</script>

<style>
</style>
