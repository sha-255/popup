<template>
  <button @click="isPopupOpen = true">Open popup</button>
  <message-popup
  :is-open="isPopupOpen">
    My someone text!
  </message-popup>
</template>

<script>
import MessagePopup from "./components/MessagePopup.vue"

export default {
  components: { MessagePopup },
  data() {
    return {
      isPopupOpen: false
    }
  },
  methods: {
    popupConfirmed() {
      alert("Confirmed")
    }
  }
}
</script>
