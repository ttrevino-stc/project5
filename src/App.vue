<script>
import { ref, provide } from 'vue';
import NavMenu from '@/components/NavMenu.vue'

export default {
  components: { NavMenu },
  setup() {
    const timeRemaining = ref(300);
    let timerInterval = null;

    const startTimer = () => {
      if (!timerInterval) {
        timerInterval = setInterval(() => {
          if (timeRemaining.value > 0) {
            timeRemaining.value--;
          } else {
            clearInterval(timerInterval);
            timerInterval = null;
          }
        }, 1000);
      }
    };

    const stopTimer = () => {
      clearInterval(timerInterval);
      timerInterval = null;
    };

    const resetTimer = () => {
      stopTimer();
      timeRemaining.value = 300;
    };

    provide('timer', { timeRemaining, startTimer, stopTimer, resetTimer });

    return {};
  }
};
</script>

<template>
  <div class="min-h-screen bg-gray-100">
    <NavMenu />
    <RouterView />
  </div>
</template>
