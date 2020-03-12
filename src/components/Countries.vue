<template>
  <div class="field has-addons flexvertical">
    <form @submit.prevent="addDestination">
      <label for="newDestination">New Destination</label>
      <div class="field is-grouped">
        <p class="control is-expanded">
          <input
            class="input is-info"
            v-model="newDestination"
            type="text"
            name="newDestination"
            id="newDestination"
            value
            placeholder="Text input"
          />
        </p>
        <p class="control">
          <button class="button is-primary" type="submit" name="button">Add</button>
        </p>
      </div>
    </form>

    <div>
      <div v-if="newDestination" class=" buttons">
        <a href="#YourTrip" class="myflex">
          <button
          class="myflex button is-small"
          v-for="country in countries.filter(country => country.name.toLowerCase().includes(newDestination.toLowerCase()))"
          :key="country.id"
          v-on:click="addDestinationButton($event)"
          v-bind:value="country.name"
          type="submit"
        >
          {{country.name}}
          <img
            :src="'https://www.countryflags.io/'+country.alpha2Code+'/flat/16.png'"
          />
        </button>
        </a>
      </div>
      <div v-else >
        <a href="#YourTrip" class="myflex">
          <button
          class="myflex button is-small"
          v-for="country in countries"
          :key="country.id"
          v-on:click="addDestinationButton($event)"
          v-bind:value="country.name"
          type="submit"
        >
          {{country.name}}
          <img
            :src="'https://www.countryflags.io/'+country.alpha2Code+'/flat/16.png'"
          />
        </button>
        </a>
      </div>
    </div>
  <!-- Here is the part of countries selected -->
    <h1 id="YourTrip">Your Trip</h1>
    <ul>
      <div class="columns is-multiline is-mobile">
      <li v-for="destination in destinations" :key="destination.key" class="column is-one-third">
        <h1><b>{{ destination.title }}</b></h1>
        <button
          class="delete is-medium"
          @click="removeDestination(destination)"
          type="button"
          name="removedestination"
        >Delete</button>
          <Flag v-bind:dest="destination.title" />
          <!-- filter with search bar to reduce choice of countries -->
          <ApolloQuery :query="require('../graphql/towns.gql')" v-bind:variable="destination">
          <template v-slot="{result: {loading, error, data}}">
            <div v-if="data">
              <div v-for="cities in data.details.filter(cities => cities.name.includes(destination.title))" :key="cities.id"> 
                <!-- show the towns of the country, you can add more infos if you add mode in the query -->
                <div class="field has-addons">
                  <div class="control is-expanded">
                    <div class="select is-fullwidth">
                      <select name="allcities" v-model="newCountry">
                      <option disabled value>See towns</option>
                      <option
                      v-for="city in cities.cities" :key="city.id"
                        v-bind:value="city.name"
                      >{{city.name}}</option>
                    </select>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </template>
        </ApolloQuery>
      </li>
      </div>
    </ul>
  </div>
</template>

<script>
import gql from "graphql-tag";
import Flag from "./Flag.vue";
export default {
  name: "Countries",
  components: {
    Flag
  },
  data() {
    return {
      newCountry: "",
      countries: [],
      details: [],
      newDestination: "",
      destinations: [],
      pays: "France",
      dest: ""
    };
  },
  apollo: {
    countries: gql`
      query {
        countries {
          name
          alpha2Code
        }
      }
    `
  },
  props: {
    msg: String
  },
  methods: {
    addCountry() {
      console.log(this.newCountry); // display live the form
      if (this.newCountry) {
        this.countries.push({
          title: this.newCountry,
          done: false
        });
      }
      this.newCountry = "";
    },

    addDestination() {
      console.log(this.newDestination); // display live the form

      // add the info in a array in data Destination[]
      if (this.newDestination) {
        this.destinations.push({
          title: this.newDestination,
          done: false
        });
      }
      // to clear the input after add an info in the list[]
      this.newTodo = "";
    },
    addDestinationButton(e) {
      console.log(e.target.value); // display live the form

      // add the info in a array in data Destination[]
      if (e.target.value) {
        this.destinations.push({
          title: e.target.value,
          done: false
        });
      }
      // to clear the input after add an info in the list[]
      this.newTodo = "";
    },
    // sdelete from the array, have to search the index first
    removeDestination(destination) {
      console.log(destination.title);
      const destinationIndex = this.destinations.indexOf(destination);
      this.destinations.splice(destinationIndex, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.myflex {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  background-color: azure;
}
.flexvertical {
  display: flex;
  flex-direction: column;
  padding: 5em 2em;
}
</style>
