<template>
  <div id="app">
    <header>
      <h1></h1>
    </header>
    <img id="logoHome" alt="Vue logo" src="./assets/logo.png" />
    <!-- video wallpaper -->
    <Video />
    <!-- search bar and small flags -->
    <Countries class="center bckgdColor" />
    <!-- examples of countries for somes ideas  -->
    <Basic msg="Vue.js " class="center bckgdColor" />
    <footer class="footer">
      <div class="content has-text-centered">
        <p>
          <strong>World travel</strong> by
          <a href="https://github.com/rim31">oseng</a>
        </p>
      </div>
    </footer>
  </div>
</template>

<script>
import Basic from "./components/Basic.vue";
import Countries from "./components/Countries.vue";
import Video from "./components/Video.vue";
export default {
  name: "App",
  components: {
    Countries,
    Video,
    Basic
  },
  data() {
    return {
      title: "World travel",
      info: null
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
header {
  height: 50px;
  background-color: aquamarine;
  text-align: center;
  vertical-align: middle;
  top: 0%;
}
footer {
  bottom: 0%;
  height: 50px;
}
.center {
  justify-content: center !important;
}

.bckgdColor {
  background-color: #ecf0f1;
  text-shadow: 2px 2px #98c593;
}
</style>
