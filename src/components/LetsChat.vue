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
    :header="state.showReply ? `Re: ${state.subject}` : 'Send me an email!'"
  >
    <div v-if="state.showReply">
      <p>You’re alive! I can see</p>
      <p>rot pressed into your screen,</p>
      <p>this world is slow breathing</p>
      <p>on its death bed of greed.</p>
      <br />
      <p>Your palms pressed to its</p>
      <p>chest, heart washed down</p>
      <p>your sleeve, comb through</p>
      <p>the mold, reignite the need.</p>
      <br />
      <p>Hold this dying home & leave</p>
      <p>daisies by the door. Lead</p>
      <p>its spirit to the riverbed, lay</p>
      <p>rest some place</p>
      <p>free.</p>
    </div>
    <div v-else>
      <p>Hey stranger, nice to meet you!</p>
      <p>Shoot me a message and I'll get back to you as soon as I'm online.</p>
      <form class="lets-chat-form" @submit.prevent="sendMessage">
        <label class="field">
          <span class="label-text">Subject</span>
          <input
            type="text"
            v-model="state.subject"
            placeholder="What's this about?"
            aria-label="Subject"
            required
          />
        </label>
        <label class="field">
          <span class="label-text">Message</span>
          <textarea
            v-model="state.message"
            placeholder="Write your message here..."
            rows="6"
            aria-label="Message"
            required
          ></textarea>
        </label>
        <div class="actions">
          <button type="submit" :disabled="sending || !canSend">
            {{ sending ? "Sending..." : "Send" }}
          </button>
        </div>
      </form>
      <div class="disclaimer">
        <i
          >* Note this does not actually send an email to the creator of this
          site & is for visual purposes only. Try re-opening this popup after
          you "send" your message ;-)</i
        >
      </div>
    </div>
  </RetroPopup>
</template>
<script setup lang="ts">
  import { reactive, ref, computed } from "vue";
  import RetroPopup from "./RetroPopup.vue";

  interface IPaywallAdState {
    showPopup: boolean;
    showReply: boolean;
    subject: string;
    message: string;
  }

  // TODO: Add a subject bar and make the response "Re: Subject"
  // and also add a fake "sending" gif with 3 second timeout

  const state = reactive<IPaywallAdState>({
    showPopup: false,
    showReply: false,
    subject: "",
    message: "",
  });

  const sending = ref(false);

  const canSend = computed(() => {
    return state.subject.trim().length > 0 && state.message.trim().length > 0;
  });

  async function sendMessage() {
    if (!canSend.value || sending.value) return;
    sending.value = true;
    try {
      await new Promise((r) => setTimeout(r, 1000));
      state.showPopup = false;
      state.showReply = true;
    } finally {
      sending.value = false;
    }
  }
</script>

<style scoped>
  .lets-chat {
    border-bottom: 2px solid black;
  }

  .lets-chat-form {
    display: flex;
    flex-direction: column;
    gap: 12px;
    margin-top: 8px;
  }

  .field {
    display: flex;
    flex-direction: column;
  }

  .label-text {
    font-size: 12px;
    margin-bottom: 6px;
  }

  input[type="text"],
  textarea {
    border: 2px solid #222;
    padding: 10px 12px;
    font-size: 14px;
    resize: vertical;
    outline: none;
    font-family: "myfont;";
  }

  .actions {
    display: flex;
    justify-content: flex-end;
  }

  button {
    background: white;
    border: 2px solid black;
    padding: 8px 14px;
    width: 100%;
    font-family: "myfont";

    :hover {
      cursor: pointer;
    }
  }

  button[disabled] {
    cursor: not-allowed;
    color: black;
    background-color: lightgray;
  }

  .disclaimer {
    margin-top: 20px;
  }
</style>
