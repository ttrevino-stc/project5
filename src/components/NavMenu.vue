<template>
  <nav class="bg-slate-900 h-20 items-center text-white">
    <RouterLink :to="{name: 'Home'}">Home</RouterLink>
    <RouterLink :to="{name: 'Other'}">Other</RouterLink>
    
    <RouterLink :to="{name: 'SettingsPage'}">Settings</RouterLink>

    <div v-if="isAuthenticated">
      Welcome {{ user.email }}
      <button @click="logout" class="rounded-md bg-red-500 px-4 py-2 mx-2 text-red-100 hover:bg-red-700">LOGOUT</button>
    </div>
    <div v-else>
      <RouterLink :to="{name: 'LoginPage'}">Login</RouterLink>
    </div>
  </nav>
  <nav class="bg-gray-900 text-white p-4 flex justify-between items-center">
    <h1 class="text-xl font-bold">Countdown Timer</h1>
    
    <div class="space-x-2">
      <button @click="startTimer" class="px-4 py-2 bg-green-500 rounded-md hover:bg-green-600">Start</button>
      <button @click="stopTimer" class="px-4 py-2 bg-red-500 rounded-md hover:bg-red-600">Stop</button>
      <button @click="resetTimer" class="px-4 py-2 bg-gray-500 rounded-md hover:bg-gray-600">Reset</button>
    </div>
  </nav>
</template>

<style lang="postcss" scoped>
nav {
  @apply flex justify-center space-x-4;

  & .router-link-active {
    @apply underline underline-offset-4;
  }
}
</style>

<script>
import { useAuth } from '../composables/useAuth';
import { inject } from 'vue';

const { isAuthenticated, logout, user } = useAuth()

export default {
  setup() {
    const { startTimer, stopTimer, resetTimer } = inject('timer');

    return { startTimer, stopTimer, resetTimer };
  }
};

</script>
