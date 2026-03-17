<template>
  <div v-if="props.visible" class="retro-backdrop" @click.stop></div>
  <div v-if="props.visible" class="retro-popup" role="dialog" aria-modal="true">
    <h2>{{ props.header }}</h2>
    <slot></slot>
    <button class="close-button" @click="onPopupClose">Close</button>
  </div>
</template>
<script setup lang="ts">
  interface RetroPopupProps {
    visible: boolean;
    header: string;
  }

  const props = defineProps<RetroPopupProps>();

  const emit = defineEmits(["update:visible"]);

  const onPopupClose = () => {
    emit("update:visible", false);
  };

  import { watch, onBeforeUnmount } from "vue";

  const restoreBody = () => {
    document.body.style.overflow = "";
  };

  watch(
    () => props.visible,
    (visible) => {
      if (visible) {
        document.body.style.overflow = "hidden";
      } else {
        restoreBody();
      }
    },
  );

  onBeforeUnmount(() => {
    restoreBody();
  });
</script>
<style scoped>
  .retro-popup {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: lightblue;
    border: 4px solid #000;
    box-shadow: 8px 8px 0px #000; /* 3D shadow */
    padding: 20px;
    padding-bottom: 64px;
    text-align: center;
    width: 500px;
    z-index: 1000;
  }

  .retro-popup h2 {
    margin-top: 0;
    border-bottom: 2px solid #000;
    padding-bottom: 10px;
  }

  .retro-popup button {
    background: #fff;
    border: 2px solid #000;
    padding: 6px 12px;
    cursor: pointer;
    font-family: inherit;
    font-size: 16px;
  }

  .retro-popup .close-button {
    position: absolute;
    right: 12px;
    bottom: 12px;
    padding: 6px 10px;
    font-size: 14px;
  }

  .retro-backdrop {
    position: fixed;
    inset: 0;
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(6px);
    -webkit-backdrop-filter: blur(6px);
    z-index: 900;
    /* capture pointer events so underlying UI is not interactable */
    pointer-events: auto;
  }
</style>
