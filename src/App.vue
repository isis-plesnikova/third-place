<template>
  <div class="container">
    <div class="body-section">
      <div id="header">
        <h1 class="header-text">Third place</h1>
      </div>
      <div class="grid-container">
        <aside class="left-column">
          <img class="lets-chat" src="/letschat.svg" width="100" height="40" />
          <img class="paywall" src="/fakead.gif" width="200" height="243" />
          <h2>Fix your face today!</h2>
          <img src="/beautypixel.png" width="200" height="243" />
        </aside>
        <main class="main-content">
          <WelcomeBox />
          <YoutubeVideo />
        </main>
        <aside class="right-column">
          <img src="/chumpgpt.gif" width="100" height="100" />
          <img src="/chumpgptad.gif" width="100" height="100" />
          <p>
            Have you ever tried working from home, but can't seem to to focus?
          </p>
          <h3>Cafes are in!</h3>
        </aside>
      </div>
    </div>
  </div>
  <RetroPopup
    v-model:visible="state.showOpeningPopup"
    @update:visible="state.showOpeningPopup = false"
  />
  <footer>
    <p>See u next time!</p>
    <!-- By
    <a
      rel="nofollow"
      class="external text"
      href="https://www.flickr.com/people/185008797@N05"
      >Real Estate Japan</a
    >
    from Tokyo, Japan -
    <a
      rel="nofollow"
      class="external text"
      href="https://www.flickr.com/photos/185008797@N05/49952811147/"
      >Yoyogi Park 5/30 weekend after state of emergency lifted in Tokyo</a
    >,
    <a
      href="https://creativecommons.org/licenses/by/2.0"
      title="Creative Commons Attribution 2.0"
      >CC BY 2.0</a
    >,
    <a href="https://commons.wikimedia.org/w/index.php?curid=90940491">Link</a> -->
  </footer>
</template>

<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./components/RetroPopup.vue";
  import YoutubeVideo from "./components/YoutubeVideo.vue";
  import WelcomeBox from "./components/WelcomeBox.vue";

  interface AppState {
    showOpeningPopup: boolean;
  }

  const state = reactive<AppState>({
    showOpeningPopup: false, // TODO: Change to true
  });
</script>

<style scoped>
  .grid-container {
    display: grid;
    /* Defines 3 columns: 
     - 300px fixed width for the left
     - '1fr' (one fraction of remaining space) for the flexible middle content
     - 300px fixed width for the right */
    grid-template-columns: 300px 1fr 300px;
    gap: 10px;
  }

  .left-column,
  .main-content,
  .right-column {
    padding: 15px;
    /* Stack and center content inside each column */
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 400px;
    height: auto;
  }

  .main-content {
    background-color: #47b779;
  }

  .left-column {
    background-color: #8babf1;
  }

  .right-column {
    background-color: #8babf1;
  }

  #header {
    /* allow header to visually lift above the main card so the
       container background shows between header and content */
    position: relative;
    z-index: 10;
    background-color: #5e4e8c;
    height: 120px;
    background-image: url("/header.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    display: flex;
    justify-content: center;
    align-items: center;
    /* pull the header up so there's visible background between
       the header and the rest of the content */
    margin-top: -28px;
    margin-bottom: 20px;
  }

  .header-text {
    color: white;
    -webkit-text-stroke-width: 2px; /* Outline width */
    -webkit-text-stroke-color: black; /* Outline color */
    font-size: 100px;
    text-align: center;
  }

  footer {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 10;
    background-color: #47b779;
    text-align: center;
    padding: 10px;
    position: relative;
    bottom: 0;
    height: 50px;
  }

  /* img {
    border: 1px solid #47b779;
  } */

  /* ensure images don't overflow their column and stay centered */
  .left-column img,
  .right-column img,
  .main-content img {
    max-width: 100%;
    height: auto;
    display: block;
    margin: 0 auto;
  }

  .body-section {
    width: 1200px;
    max-width: 100%;
    /* center the content and leave a visible gap of the container
       background around it */
    margin: 40px auto;
    padding: 18px;
  }

  .lets-chat {
    border-bottom: 2px solid black;
    &:hover {
      border-bottom: none;
      padding-bottom: 2px;
    }
  }

  .paywall {
    padding-top: 20px;
  }
</style>
