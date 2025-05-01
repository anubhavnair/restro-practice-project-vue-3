<template>
 <RouterView></RouterView>
</template>

<script>

import UserSignUpView from './views/UserSignUpView.vue';
import { RouterView,RouterLink } from 'vue-router';

export default {
  name: "App",
  components: {
    UserSignUpView
  },
  data() {
    return {
      // Your data here
    };
  },
  methods: {
    // Your methods here
  }
};
</script>

<style scoped>
/* Your styles here */
</style>