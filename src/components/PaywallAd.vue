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
    header="Paywall"
  >
    <p>I’m starving</p>
    <p>for that Benjamin folded</p>
    <p>in your leather wallet. I’m there</p>
    <p>in your rearview, watch me</p>
    <p>creep into the corner</p>
    <p>of everything.</p>
    <br />
    <p>I’ll crack you a deal –</p>
    <p>It’s free for ten days,</p>
    <p>can’t pass it up &</p>
    <p>I’ll only call every month,</p>
    <p>or every three.</p>
    <br />
    <p>Oh the burden</p>
    <p>to own.</p>
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
