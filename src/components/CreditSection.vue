<template>
  <div class="poem credits" @click="state.showPopup = true">
    <img src="/click4credits.gif" />
  </div>
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="Citations / Credits"
  >
    Background photo by
    <a
      rel="nofollow"
      class="external text"
      href="https://www.flickr.com/people/185008797@N05"
      >Real Estate Japan</a
    >
    from Tokyo, Japan -
    <a
      rel="nofollow"
      class="external text"
      href="https://www.flickr.com/photos/185008797@N05/49952811147/"
      >Yoyogi Park 5/30 weekend after state of emergency lifted in Tokyo</a
    >,
    <a
      href="https://creativecommons.org/licenses/by/2.0"
      title="Creative Commons Attribution 2.0"
      >CC BY 2.0</a
    >,
    <a href="https://commons.wikimedia.org/w/index.php?curid=90940491">Link</a>
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
  .credits {
    margin-top: 30px;
  }
</style>
