<template>
  <section class="main fullscreen">
    <video
      controls
      poster="../assets/coverr.jpg"
      onmouseover="this.play()"
      onmouseout="this.pause();this.currentTime=0;"
      class="videoFooter intro"
      autoplay
      muted
      loop
    >
      <img class="myPreview2 showme" src="../assets/coverr.jpg" alt="paris" />
      <source src="../assets/coverr.mp4" type="video/mp4" />Your browser does not support the video tag. I suggest you upgrade your browser
    </video>
    <div class="content message">
      <header style="display:block;">
        <h1>{{title}}</h1>
        <p style="text-shadow:1px 1px #000000">
          Welcome to
          <strong class="rim">{{title}}.</strong> Plan your next trip, look at different countries
          <br />
          Search a country or click on one
        </p>
        <br />
      </header>
    </div>
  </section>
</template>

<script>


export default {
  name: "Coucou",
  data() {
    return {
      title: "World Travel"
    };
  }
};
</script>
<style>
.center {
  justify-content: center !important;
}
.showme {
  display: block;
  -webkit-animation: disappear 2s;
  animation: disappear 2s;
  -webkit-transition-delay: 2s;
  transition-delay: 2s;
}
.intro {
  background-size: 256px 256px, cover;
  background-attachment: fixed, fixed;
  background-position: top left, bottom center;
  background-repeat: repeat, no-repeat;
}
.videoFooter {
  position: fixed;
  top: 50%;
  left: 50%;
  min-width: 100%;
  min-height: 100%;
  width: auto;
  height: auto;
  z-index: -1;
  transform: translateX(-50%) translateY(-50%);
  background-size: cover;
  transition: 1s opacity;
}
.rim {
	color: #ecf0f1;
	text-shadow: 2px 2px #98c593
}
.message {
  background-color:  #ecf0f1;;
}
</style>