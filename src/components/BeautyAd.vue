<template>
  <div class="poem container" @click="state.showPopup = true">
    <h2>Yuck! Fix your face today!</h2>
    <img src="/beautypixel.png" width="200" height="243" />
  </div>
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="Self Care"
  >
    <p>self care poem</p>
  </RetroPopup>
</template>
<script setup lang="ts">
  import { reactive } from "vue";
  import RetroPopup from "./RetroPopup.vue";

  interface IBeautyAdState {
    showPopup: boolean;
  }

  const state = reactive<IBeautyAdState>({ showPopup: false });
</script>
<style scoped>
  .container {
    border: 5px ridge black;
    background-color: #b9ccf7;
    padding: 10px;
    margin: 20px;

    h2 {
      font-size: 30px;
    }
  }
</style>
