# Vue JS + graphQL

## installation Vue/cli 
https://cli.vuejs.org

```
yarn global add @vue/cli
# OR
npm install -g @vue/cli
```

```
vue create vuegraphql
# OR
vue ui
```
select default + yarn or whatever u like

Installation Axios

```
cd vuegraphql
yarn serve
npm install axios --save
```

add apollo to connect to a graphQL DB
```
npm i @vue/cli-shared-utils
vue add apollo
```
say yes for exemple and No for the server, No again


supprimer les fichiers dans /graphql

modifier le fichier vue-apollo.js :
en changeant le endpoint et wspoint
```
...
// Http endpoint
// const httpEndpoint = process.env.VUE_APP_GRAPHQL_HTTP || 'http://localhost:4000/graphql'//original
const httpEndpoint = process.env.VUE_APP_GRAPHQL_HTTP || 'https://api.graph.cool/simple/v1/swapi'
// Files URL root
export const filesRoot = process.env.VUE_APP_FILES_ROOT || httpEndpoint.substr(0, httpEndpoint.indexOf('/graphql'))

Vue.prototype.$filesRoot = filesRoot

// Config
const defaultOptions = {
  // You can use `https` for secure connection (recommended in production)
  httpEndpoint,
  // You can use `wss` for secure connection (recommended in production)
  // Use `null` to disable subscriptions
  // wsEndpoint: process.env.VUE_APP_GRAPHQL_WS || 'ws://localhost:4000/graphql',//original
  wsEndpoint: null,
  ...
```
https://fakerql.com/graphql ne fonctionne plus, le remplacer par celui-ci : https://medium.com/@notrab/fakerql-is-ultimate-graphql-endpoint-for-fake-data-bd83f4cd6ad1
https://graphql.org/swapi-graphql

https://www.graphqlbin.com/v2/6RQ6TM
endpoint is there : 
https://api.graph.cool/simple/v1/swapi
data of star wars

https://api.spacexdata.com/v2/



other graphQL
https://us1.prisma.sh/erik-hanchett-01ee5/server/dev
from 
https://www.youtube.com/watch?v=W_xft6HZecQ

## how to get data with graphQL

### 1 - in the component helloworld.vue

add in the script part :
 ```
 <script>
import gql from "graphql-tag";
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  apollo: {
    allPersons: gql`
    query {
      allPersons {
        name
      }
    }`
  }
};
</script>
```

display the result above :

```
  <div v-for="person in allPersons" :key="person.id">
      {{person.name}}
  </div>
```



### 2 - create a file.gql in /graphql


### 3 - AXIOS : 


## Flags

https://www.countryflags.io/

concatenate variable into url string
```
<img :src="'https://www.countryflags.io/'+city.country.alpha2Code+'/flat/64.png'" />
```
