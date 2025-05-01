<template>
  <div class="w-full flex justify-center h-screen items-center">
    <div class="bg-amber-400 p-4 rounded-2xl overflow-hidden min-h-[90%]">
      <div class="flex justify-center">
        <img
          class="w-30"
          src="https://png.pngtree.com/png-clipart/20200727/original/pngtree-restaurant-logo-design-vector-template-png-image_5441058.jpg"
          alt=""
        />
      </div>
      <h1 class="text-center text-2xl font-semibold underline">Sign Up Here</h1>
      <div class="flex justify-center mt-2">
        <form @submit.prevent="handleSubmit">
          <div class="flex items-center gap-2 justify-between">
            <label for="name" class="text-lg">Enter Your Name :</label>
            <input
              v-model="user.name"
              type="text"
              name="name"
              id="name"
              placeholder="Your Name"
              class="border-1 border-blue-black py-2 pl-2 mt-2 rounded-xl"
            />
          </div>
          <div class="flex items-center gap-2 justify-between">
            <label for="email" class="text-lg">Enter Your Email :</label>
            <input
              v-model="user.email"
              type="email"
              name="email"
              id="email"
              placeholder="example@gmail.com"
              class="border-1 border-blue-black py-2 pl-2 mt-2 rounded-xl"
            />
          </div>
          <div class="flex items-center gap-2 justify-between">
            <label for="password" class="text-lg">Enter Your Password :</label>
            <input
              v-model="user.password"
              type="password"
              name="password"
              id="password"
              placeholder="password"
              class="border-1 border-blue-black py-2 pl-2 mt-2 rounded-xl"
            />
          </div>
          <div class="flex justify-center mt-4">
            <button
              class="bg-green-800 hover:bg-black cursor-pointer text-white p-2 rounded-xl font-normal"
            >
              Signup
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "UserSignUp",
  data() {
    return {
      user: {
        name: "",
        email: "",
        password: "",
      },
    };
  },
  methods: {
    // Your methods here
    async handleSubmit() {
      // Handle form submission logic here
      //   console.log("Form submitted:", this.user);
      const user = await axios.post("http://localhost:3000/user", this.user);

      localStorage.setItem("user-info", JSON.stringify(user.data));  
      this.user = {
        name: "",
        email: "",
        password: "",
      };
        this.$router.push({ name: "home" });
    },
  },
};
</script>

<style>
/* Your styles here */
</style>
