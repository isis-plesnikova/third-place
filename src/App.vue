<template>
  <div class="container">
    <div class="body-section">
      <div id="header">
        <h1 class="header-text">Third place</h1>
      </div>
      <div class="grid-container">
        <aside class="left-column">
          <img class="wander" src="/wander.gif" alt="Wander illustration" />
          <LetsChat />
          <PaywallAd />
          <BeautyAd />
        </aside>
        <main class="main-content">
          <WelcomeBox />
          <div class="dialogue-wrapper" role="img" aria-label="dialogue images">
            <img
              class="dialogue"
              src="/dialogue.png"
              width="400"
              height="1600"
              alt=""
              aria-hidden="true"
            />
            <img
              class="dialogue2"
              src="/dialogue2.png"
              width="400"
              height="1600"
              alt=""
              aria-hidden="true"
            />
          </div>
          <YoutubeVideo />
        </main>
        <aside class="right-column">
          <ChumpGpt />
          <ShortForm />
          <CafeAd />
          <CreditSection />
        </aside>
      </div>
    </div>
  </div>
  <RetroPopup
    v-model:visible="state.showOpeningPopup"
    header="FIRST / SECOND / THIRD"
    @update:visible="state.showOpeningPopup = false"
  >
    <div style="text-align: center">
      <p>First: Home, bed</p>
      <p>sleep. Heart, steep</p>
      <p>tea dream cook clean.</p>
      <br />
      <p>Second: Worker</p>
      <p>bee, think. Be work,</p>
      <p>coffee drink, buzz,</p>
      <p>meet.</p>
      <br />
      <p>Third: ???</p>
      <i>NOTE: Please view site on desktop.</i>
    </div>
  </RetroPopup>
  <footer>
    <p>See u next time!</p>
  </footer>
</template>

<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./components/RetroPopup.vue";
  import YoutubeVideo from "./components/YoutubeVideo.vue";
  import WelcomeBox from "./components/WelcomeBox.vue";
  import BeautyAd from "./components/BeautyAd.vue";
  import CafeAd from "./components/CafeAd.vue";
  import ChumpGpt from "./components/ChumpGpt.vue";
  import ShortForm from "./components/ShortForm.vue";
  import PaywallAd from "./components/PaywallAd.vue";
  import LetsChat from "./components/LetsChat.vue";
  import CreditSection from "./components/CreditSection.vue";

  interface AppState {
    showOpeningPopup: boolean;
  }

  const state = reactive<AppState>({
    showOpeningPopup: true,
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

  .body-section {
    width: 1200px;
    max-width: 100%;
    /* center the content and leave a visible gap of the container
       background around it */
    margin: 40px auto;
    padding: 18px;
  }

  /* Dialogue hover swap: show dialogue.png by default, swap to dialogue2.png on hover */
  .dialogue-wrapper {
    display: inline-block;
  }

  .dialogue-wrapper .dialogue2 {
    display: none;
  }

  .dialogue-wrapper:hover .dialogue {
    display: none;
  }

  .dialogue-wrapper:hover .dialogue2 {
    display: block;
  }

  .wander {
    padding-bottom: 20px;
  }
</style>
