<template>
  <div class="container">
    <div id="header">
      <div class="header-text">Third place</div>
    </div>
    <div class="grid-container">
      <aside class="left-column">Left Column Content</aside>
      <main class="main-content">Main Content (Middle)</main>
      <aside class="right-column">Right Column Content</aside>
    </div>
  </div>
  <RetroPopup
    v-model:visible="state.showOpeningPopup"
    @update:visible="state.showOpeningPopup = false"
  />
  <footer>
    <p>See u next time!</p>
  </footer>
</template>

<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./components/RetroPopup.vue";

  interface AppState {
    showOpeningPopup: boolean;
  }

  const state = reactive<AppState>({
    showOpeningPopup: false, // TODO: Change to true
  });
</script>

<style scoped>
  .container {
    /* margin: 0 auto; */
    background-color: orange;
  }

  .grid-container {
    display: grid;
    /* Defines 3 columns: 
     - 300px fixed width for the left
     - '1fr' (one fraction of remaining space) for the flexible middle content
     - 300px fixed width for the right */
    grid-template-columns: 300px 1fr 300px;
    gap: 20px; /* Adds space between columns */
  }

  .left-column,
  .main-content,
  .right-column {
    padding: 15px;
    background-color: #f0f0f0;
    border: 2px solid #ccc;
    height: 100vh;
  }

  #header {
    top: 0;
    left: 0;
    right: 0;
    width: 100%; /* Ensures it spans the full width */
    z-index: 10; /* Ensures it's above other content */
    width: 100%;
    background-color: #5e4e8c;
    height: 200px;
    background-image: url("/header.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    display: flex;
    justify-content: center; /* Centers horizontally */
    align-items: center; /* Centers vertically */
  }

  .header-text {
    color: white; /* Text fill color */
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
    width: 100%; /* Ensures it spans the full width */
    z-index: 10; /* Ensures it's above other content */
    background-color: lightblue;
    text-align: center;
    padding: 10px;
    position: relative;
    bottom: 0;
    width: 100%;
    height: 50px;
  }
</style>
