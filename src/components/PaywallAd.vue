<template>
  <img
    class="paywall poem"
    src="/fakead.gif"
    width="200"
    height="243"
    @click="state.showPopup = true"
  />
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="Ownership"
  >
    <p>Own it?</p>
  </RetroPopup>
</template>
<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./RetroPopup.vue";

  interface IPaywallAdState {
    showPopup: boolean;
  }

  const state = reactive<IPaywallAdState>({ showPopup: false });
</script>

<style scoped>
  .paywall {
    padding-top: 20px;
  }
</style>
