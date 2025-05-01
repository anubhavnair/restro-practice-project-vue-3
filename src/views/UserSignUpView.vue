<template>
  <div class="user-signup-view">
    
    <UserSignUp/>
  </div>
</template>

<script>
import UserSignUp from "@/components/UserSignUp.vue";
export default {
  name: "UserSignUpView",
    components: {
        UserSignUp,
    },
  data() {
    return {
      // Your data here
    };
  },
  methods: {
    // Your methods here
  },
};
</script>

<style scoped>
/* Your styles here */
</style>
