<template>
  <img
    class="poem"
    src="/shortform.gif"
    width="200"
    height="800"
    @click="state.showPopup = true"
  />
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="The Glass"
  >
    <p>Ur face looks gr8 when u doomscroll, diva ;)</p>
    <p>Make out with dopamine like you’re dying,</p>
    <br />
    <p>light up those fingertips, it’s endless</p>
    <p>& more like a hot kiss from God.</p>
    <br />
    <p>Increased your scream time this week</p>
    <p>No not screen – it’s okay,</p>
    <br />
    <p>I thought you’d be over</p>
    <p>checking numbers by now.</p>
    <br />
    <p>Pinterest board titled NYC,</p>
    <p>like you’ll ever leave the glass.</p>
  </RetroPopup>
</template>
<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./RetroPopup.vue";

  interface IShortFormState {
    showPopup: boolean;
  }

  const state = reactive<IShortFormState>({ showPopup: false });
</script>
<style scoped>
  img {
    max-width: 100%;
    height: auto;
    display: block;
    margin: 0 auto;
    margin-bottom: 20px;
  }
</style>
