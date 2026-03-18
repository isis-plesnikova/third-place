<template>
  <div class="poem chumpgpt" @click="state.showPopup = true">
    <img src="/chumpgpt-pingpong.gif" width="100" height="100" />
    <img src="/chumpgptad.gif" width="100" height="100" />
  </div>
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="Dead water"
  >
    <p>Spoon full of your hometown:</p>
    <p>He swallows the 7-Eleven,</p>
    <p>next to the road bend by your childhood</p>
    <p>bedroom. He drinks</p>
    <p>up floorboards, cupboards,</p>
    <p>to taste how your hands</p>
    <p>move, how they cut</p>
    <p>mom’s white onions, wipe salted water</p>
    <p>from your eyelids, slice your thumb</p>
    <p>on knife’s edge, he will learn</p>
    <p>how you bleed</p>
    <p>how your heart speaks to your</p>
    <p>brain. He will slurp your synapses,</p>
    <p>turn his cells into a portrait</p>
    <p>of you.</p>
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
<style scoped>
  .chumpgpt {
    margin-bottom: 20px;
  }
</style>
