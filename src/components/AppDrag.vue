<template>
  <div draggable @dragenter.prevent @dragover.prevent @dragstart.self="onDrag">
    <slot />
  </div>
</template>
<script>
export default {
  props: {
    transferData: {
      type: Object,
      required: true
    }
  },
  methods: {
    onDrag(e) {
      e.dataTransfer.effectAllowed = "move";
      e.dataTransfer.dropEffect = "move";
      e.dataTransfer.setData("payload", JSON.stringify(this.transferData));
    }
  }
};
</script>
