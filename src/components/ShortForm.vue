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
    <p>
      Your face looks gr8 when u doomscroll, grl ;-) Make out with dopamine like
      you’re dying together joy is endless & more like a hot kiss from God
      Increased your scream time this week No not screen – it’s okay, I thought
      you’d be over checking numbers by now Pinterest board titled NYC Like
      you’ll ever leave the glass
    </p>
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
