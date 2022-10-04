<template>
  <Buttons @click="showModal"></Buttons>
  <Modal v-model:show="modalVisible">
    <Form></Form>
  </Modal>
</template>

<script>
import Buttons from "./components/UI/Buttons.vue"
import Modal from "./components/UI/Modal.vue";
import Form from "./components/UI/Form.vue";

export default {
  components: {
    Buttons,
    Modal,
    Form,
  },
  data() {
    return {
      modalVisible: false,
    }
  },
  methods: {
    showModal() {
      this.modalVisible = true;
    }
  }
}

</script>

<style>

</style>