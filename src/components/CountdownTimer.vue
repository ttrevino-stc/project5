<script>
import { inject, computed } from 'vue';

export default {
  setup() {
    const { timeRemaining } = inject('timer');

    const formattedTime = computed(() => {
      const minutes = Math.floor(timeRemaining.value / 60);
      const seconds = timeRemaining.value % 60;
      return `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
    });

    return { formattedTime };
  }
};
</script>

<template>
<div class="text-2xl font-bold text-center mt-2 text-gray-800">
    {{ formattedTime }}
  </div>

</template>