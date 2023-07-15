<template>
  <button @click="openPopup">Open popup</button>
  <message-popup
    :is-open="isPopupOpen"
    @ok="popupConfirmed"
    @close="isPopupOpen = false"
  >
    My someone text!
    <template #actions="{ confirm }">
      Write
      <input :placeholder="$options.CONFIRMATION_TEXT" v-model="confirmation" />
      &nbsp;
      <button @click="confirm" :disabled="!isConfirmationCorrect">Ok</button>
    </template>
  </message-popup>
</template>

<script>
import MessagePopup from "./components/MessagePopup.vue";

export default {
  components: { MessagePopup },
  data() {
    return {
      isPopupOpen: false,
      confirmation: "",
    };
  },
  CONFIRMATION_TEXT: "qqw",
  computed: {
    isConfirmationCorrect() {
      return this.confirmation === this.$options.CONFIRMATION_TEXT;
    },
  },
  methods: {
    openPopup() {
      this.confirmation = "";
      this.isPopupOpen = true;
    },
    popupConfirmed() {
      alert("Confirmed");
      this.isPopupOpen = false;
    },
  },
};
</script>
