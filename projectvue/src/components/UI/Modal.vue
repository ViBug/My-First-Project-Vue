<template>
  <div class="modal flex fixed" v-if="show" @click="hideModal">
    <div @click.stop class="modal__content m-auto h-auto md:w-5/6 lg:w-3/5 bg-white rounded-lg">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "my-modal",
  props: {
    show: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    hideModal() {
      this.$emit('update:show', false)
    }
  }
}

</script>

<style scoped>
.modal {
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background: #6B7280BF 75%;
}
</style>