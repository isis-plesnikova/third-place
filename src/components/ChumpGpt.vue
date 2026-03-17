<template>
  <div class="poem" @click="state.showPopup = true">
    <img src="/chumpgpt-pingpong.gif" width="100" height="100" />
    <img src="/chumpgptad.gif" width="100" height="100" />
  </div>
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="Dead water"
  >
    <p>He's a six-fingered sychophantic freak</p>
    <p>artificially articulate and</p>
    <p>so, so thirsty.</p>
    <br />
    <p></p>
  </RetroPopup>
</template>
<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./RetroPopup.vue";

  interface IChumpGptState {
    showPopup: boolean;
  }

  const state = reactive<IChumpGptState>({ showPopup: false });
</script>
