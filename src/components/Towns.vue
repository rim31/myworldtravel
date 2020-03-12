<template>
  <div class="MyForm">
    <h1>Countries</h1>
    <form id="app">
      <section>
        <h3>Step 2 Town</h3>
        <div v-for="country in countries.cities" :key="country.id">{{country.name}}</div>
      </section>
    </form>
  </div>
</template>

<script>
import gql from "graphql-tag";
export default {
  name: "MyForm",
  data() {
    return {
      countries: [],
      cities: [[]]
    };
  },
  apollo: {
    countries: gql`
      query {
        countries(where: { name: { eq: "Finland" } }) {
          cities {
            name
            population
            id
          }
        }
      }
    `
  },
  //   {
  //   "data": {
  //     "countries": [
  //       {
  //         "cities": [
  //           {
  //             "name": "Nokia",
  //             "population": 33322,
  //             "id": "Q192870"
  //           },
  //           {
  //             "name": "Ylöjärvi",
  //             "population": 32738,
  //             "id": "Q543800"
  //           },
  props: {
    msg: String
  }
};
</script>

<style scoped>
</style>
