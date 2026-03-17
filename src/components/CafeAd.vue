<template>
  <div class="poem container" @click="state.showPopup = true">
    <p>Have you ever tried working from home, but can't seem to to focus?</p>
    <p class="ad-tag"><i>Cafes are in!</i></p>
    <img class="ad-image" src="/coffeecompress.png" width="205" height="200" />
  </div>
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="There's no place for me anymore"
  >
    <p>Coffee shop hot spot</p>
    <p>lights are on. I solved the Wordle</p>
    <p>in two guesses the answer was</p>
    <p><b>THEFT.</b> We went to cafes</p>
    <p>when we were fifteen</p>
    <p>or so to chat about the world</p>
    <p>and how we’d work some hot shot jobs</p>
    <p>like Miranda Priestly.</p>
    <p>Now you’re in San Francisco and I’m in</p>
    <p>this place called <i>The Bean</i> which feels</p>
    <p>weirdly sexual to me but I shouldn’t say that</p>
    <p>I’m in the middle of reading this company</p>
    <p>report but Excel is blowing up and my oat milk</p>
    <p>latte is too sweet and it was $7,</p>
    <p>I didn’t tip.</p>
  </RetroPopup>
</template>
<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./RetroPopup.vue";

  interface ICafeAdState {
    showPopup: boolean;
  }

  const state = reactive<ICafeAdState>({ showPopup: false });
</script>
<style scoped>
  .container {
    border: 2px dashed black;
    background-color: #b9ccf7;
    padding: 10px;
    margin: 20px;
    font-size: 20px;
  }

  .poem .ad-tag {
    margin: 8px 0 0 0;
  }

  .poem .ad-image {
    display: block;
    margin-top: 8px;
  }
</style>
