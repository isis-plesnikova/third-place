<template>
  <!--TODO: Component-->
  <div v-if="state.showOpeningPopup" class="retro-popup">
    <h2>THIRD PLACE</h2>
    <button @click="onPopupClose">x</button>
    <p>First: Home, bed,
      sleep. Heart, steep
      tea dream cook
      clean 

      Second: Worker bee,
      think. Be work,
      drink coffee, buzz,
      meet 

      Third: ???
    </p>
</div>
</template>

<script setup lang="ts">
import { reactive } from 'vue';

  interface AppState {
    showOpeningPopup: boolean;
  };

  const state = reactive<AppState>({
    showOpeningPopup: true  ,
  });

  const onPopupClose = () => {
    state.showOpeningPopup = false;
  };
</script>

<style scoped>
  .retro-popup {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: yellow;
    border: 4px solid #000;
    box-shadow: 8px 8px 0px #000; /* 3D shadow */
    padding: 20px;
    font-family: 'Courier New', Courier, monospace;
    font-weight: bold;
    text-align: center;
    width: 300px;
    z-index: 1000;
  }
  .retro-popup h2 {
    margin-top: 0;
    border-bottom: 2px solid #000;
    padding-bottom: 10px;
  }
  .retro-popup button {
    background: #fff;
    border: 2px solid #000;
    padding: 5px 15px;
    cursor: pointer;
    font-family: inherit;
  }
</style>
