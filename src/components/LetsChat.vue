<template>
  <img
    class="lets-chat poem"
    src="/letschat.svg"
    width="100"
    height="40"
    @click="state.showPopup = true"
  />
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="Send me an email!"
  >
    <p>Hey stranger, welcome to third place :-)</p>
    <p>Shoot me a message and I'll get back to you as soon as I'm online.</p>
    <textarea></textarea>
    <button>Send</button>
  </RetroPopup>
</template>
<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./RetroPopup.vue";

  interface IPaywallAdState {
    showPopup: boolean;
  }

  // TODO: Add a subject bar and make the response "Re: Subject"
  // and also add a fake "sending" gif with 3 second timeout

  const state = reactive<IPaywallAdState>({ showPopup: false });
</script>

<style scoped>
  .lets-chat {
    border-bottom: 2px solid black;
  }

  button:hover {
    cursor: pointer;
  }
</style>
