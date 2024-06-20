<template>
  <li>
    <div>{{ task.name }} - {{ index }}</div>
    <div>
      <slot></slot>
    </div>
    <button @click="emitDeleteClicked()">X</button>
  </li>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TaskItem',
  props: ['task', 'index'],
  methods: {
    emitDeleteClicked() {
      this.$emit('deleteRequested', this.index)
    }
  }
})
</script>

<style></style>
