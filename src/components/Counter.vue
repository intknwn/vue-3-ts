<script setup lang="ts">
import { ref, onMounted } from 'vue';
import ControlBar from './ControlBar.vue';
import fetchCount from '../fetchCount';

interface Props {
  limit: number;
  messageOnLimit?: string;
}

const props = withDefaults(defineProps<Props>(), {
  messageOnLimit: 'The limit is reached',
});

const count = ref<number | null>(null);

onMounted(() => {
  fetchCount((initialCount) => {
    count.value = initialCount;
  });
});

function addCount(num: number) {
  if (count.value !== null) {
    if (count.value >= props.limit) {
      alert(props.messageOnLimit);
    } else {
      count.value += num;
    }
    count.value += num;
  }
}
</script>

<template>
  <div>
    <p>{{ count }}</p>
  </div>
  <ControlBar @add-count="addCount" @reset-count="count = 0" />
</template>

<style lang="scss" scoped></style>
