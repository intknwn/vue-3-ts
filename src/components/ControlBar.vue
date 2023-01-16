<script setup lang="ts">
const emit = defineEmits<{
  (e: 'add-count', n: number): void;
  (e: 'reset-count'): void;
}>();
</script>

<template>
  <div>
    <p>
      <button @click="emit('add-count', 1)">Add</button>
      <button @click="emit('reset-count')">Reset</button>
    </p>
  </div>
</template>

<style lang="scss" scoped></style>
