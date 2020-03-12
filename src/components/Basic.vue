<template>
  <!-- just some examples to help to choose a country -->
  <div class="Basic">
    <label for="newDestination">Ideas for Destination</label>
    <div class="columns is-multiline is-mobile">
      <!-- data of the query graphQL in the variable cities -->
      <div v-for="city in cities" :key="city.id" class="column is-one-fifth">
        <article class="tile is-child notification is-link is-light">
          <p class="title">{{city.name}}</p>
          <p class="subtitle">{{city.population}} pers</p>
          <p class="subtitle">
            <b>{{city.country.name}}</b>
            , {{city.country.capital.name}}
          </p>
          <figure class="image is-8by8">
            <img :src="'https://www.countryflags.io/'+city.country.alpha2Code+'/flat/64.png'" />
          </figure>
        </article>
      </div>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
export default {
  name: "Basic",
  data() {
    return {
      cities: [],
    };
  },
  props: {
    msg: String
  },
  apollo: {
    cities: gql`
      query {
        cities(limit: 10) {
          name
          population
          country {
            name
            alpha2Code
            capital {
              id
              name
            }
          }
        }
      }
    `
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
