<template>
  <div class="poem container" @click="state.showPopup = true">
    <h2>Yuck! Fix your face today!</h2>
    <img
      src="/beautypixel.png"
      width="200"
      height="243"
      alt="Beauty product ad image (click to open)"
    />
  </div>
  <RetroPopup
    v-model:visible="state.showPopup"
    @update:visible="state.showPopup = false"
    header="Self Care"
  >
    <p>Your skin’s lookin’ droopy, baby,</p>
    <p>wanna scrape it? Drain</p>
    <p>those lymph nodes</p>
    <p>with this jade Gua Sha I got</p>
    <p>from Target.</p>
    <br />
    <p>I can see that blackhole</p>
    <p>living on your forehead.</p>
    <p>Can I rub some Korean snail</p>
    <p>mucin all over</p>
    <p>your rosy scales?</p>
    <p>I promise your cheeks</p>
    <p>will turn to glass.</p>
    <br />
    <p>Can I give you</p>
    <p>my star-shaped pimple</p>
    <p>patches? They’re baby blue,</p>
    <p>built to suck your oils,</p>
    <p>whiten your teeth,</p>
    <p>clean your blood,</p>
    <p>kiss your children goodnight.</p>
    <br />
    <p>I ordered you a forty-six</p>
    <p>dollar Pink Unicorn Whipped</p>
    <p>Face Cream. You can really</p>
    <p>apply it anywhere,</p>
    <p>it’s vegan. You’re vegan,</p>
    <p>right?</p>
    <br />
    <p>Trust me, you’ll love</p>
    <p>this triple-kale protein soda,</p>
    <p>I’ll toss in some spirulina</p>
    <p>& sunscreen</p>
    <p>pills,</p>
    <p>with this GLP-1 B-12 antioxidant</p>
    <p>powder, as a bonus.</p>
    <p>Are you feeling whole?</p>
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
