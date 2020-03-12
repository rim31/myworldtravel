<template>
  <div class="Flag">
    <div v-bind:v-if="dest">
       <ApolloQuery :query="require('../graphql/flag.gql')" v-bind:variable="dest">
        <template v-slot="{result: {loading, error, data}}">
        <div v-if="data">
            <div v-for="country in data.flag.filter(country => country.name.includes(dest))" :key="country.id">
                <div class="notification is-primary is-light">
                <article class="tile is-child notification is-white is-light">
                    <p class="title">{{country.name}}</p>
                    <p class="subtitle">{{country.capital.name}}</p>
                    <p class="subtitle">{{country.capital.country.population}} pers</p>
                    <p class="subtitle"><b>{{country.capital.country.alpha2Code}}</b></p>
                <figure class="image is-8by8">
                    <img :src="'https://www.countryflags.io/'+country.capital.country.alpha2Code+'/flat/64.png'" />
                </figure>
                    </article>
                <p>GPS : {{country.capital.country.location.lat}}, 
                {{country.capital.country.location.long}}</p>
            </div>
            </div>
        </div>
        </template>
        </ApolloQuery>
    </div>

  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      cities: [],
      favorite: [],
      title: "Simple Destinations list vue js",
      newDestination: "",
      destinations: [],
      myCountry: "France",
      flag: []
    };
  },
  props: {
    msg: String,
    dest: String
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
