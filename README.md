# Vue JS + graphQL

## Run

Please install Docker first:

https://www.docker.com/

Run this cmd :
```
docker build -t vuejs-loft/dockerize-vuejs-app .

docker run -it -p 8080:8080 --rm --name dockerize-vuejs-app-1 vuejs-loft/dockerize-vuejs-app

```

if your don' have docker but environnement node,vue Js , graphql installed

run on a terminal :
```
yarn serve

```
go to :
http://localhost:8080/

You can use the website. Have FUN !





## Create a new project : Vue/cli graphql
https://cli.vuejs.org


### How to create a vue/cli graphQL project
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

Add apollo to connect to a graphQL DB
```
npm i @vue/cli-shared-utils
vue add apollo
```
say yes for exemple and No for the server, No again

edit files in /graphql

Modify file vue-apollo.js :
Modify  endpoint & wspoint
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

![alt text](https://github.com/rim31/myworldtravel/blob/master/src/assets/page4.png?raw=true)

## how to get data with graphQL

###  Query example in component 

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

< ! > 
the query of this graphQL server doesn't give you enough options to select informations you want. It gives you too much

### TIPS :

#### Flags

https://www.countryflags.io/

concatenate variable into url string
example flag iamge
```
<img :src="'https://www.countryflags.io/'+city.country.alpha2Code+'/flat/64.png'" />
```


#### Search bar

function filter in javascript:

https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/filter



# With more time :

## beautiful image of country

## Add a map
add a map to display countris on a world map

## Redux
use flux 


