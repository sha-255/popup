<template>
  <button @click="popupLogic">Open popup</button>
  <message-popup ref="confirmationPopup">
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
    async popupLogic() {
      this.confirmation = "";
      const popupResult = await this.$refs.confirmationPopup.open();
      if (popupResult) {
        alert("Confirmed");
      }
    },
  },
};
</script>
